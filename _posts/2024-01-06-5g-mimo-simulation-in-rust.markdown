---
layout: post
title: "5G MIMO algorithm simulations in Rust!"
date: 2024-01-06 15:58:00 +0100
categories: projects
math: true
---

## 5G Wireless Communication
### 5G
5G, the fifth generation of cellular network technology, is a significant upgrade over its predecessors:

1. **Super-fast**: Imagine downloading a movie in seconds! 5G boasts significantly faster data speeds compared to 4G, enabling seamless streaming, high-resolution video calls, and near-instantaneous downloads.
1. **Ultra-low latency**: Think responsive apps and real-time interactions. 5G minimizes the lag between data transmission and response, crucial for applications like self-driving cars, telemedicine, and virtual reality.
1. **Increased capacity**: More and more devices can connect and share data seamlessly. 5G can handle the ever-growing demand for connectivity from billions of smartphones, connected homes, connected manufacturing equipment, and smart cities.
1. **Greater reliability**: Say goodbye to dropped calls and unreliable connections. 5G ensures a more stable and dependable network experience even in crowded areas.
1. **Unlocking new possibilities**: 5G opens doors for innovative applications beyond our current imagination. This includes the Internet of Things (IoT), where everyday objects become connected and communicate with each other, leading to smarter cities, digital industries, and enhanced everyday experiences.

### 5G algorithms
1. **Channel Modeling**: Develop a channel model that accurately simulates the characteristics of a 5G MIMO channel, including path loss, fading, and interference. This model will be used to generate realistic channel conditions.


2. **MIMO Signal Processing**: Implement key MIMO signal processing techniques, such as beamforming, spatial multiplexing, and diversity combining. These techniques are essential for improving the performance and reliability of MIMO systems.


3. **Error Control Coding**: Incorporate error control coding (ECC) schemes, such as turbo codes and LDPC codes, into your simulation. ECC is used to protect data from errors that may occur during transmission over the wireless channel.


4. **Modulation and Demodulation**: Implement modulation and demodulation techniques, such as QAM, PAM, and OFDM, to convert digital data into signals that can be transmitted over the wireless channel.


5. **Link Adaptation**: Develop link adaptation algorithms that dynamically adjust the modulation scheme, coding rate, and transmit power based on the current channel conditions. This will help to optimize the performance of the MIMO system in different scenarios.


6. **Performance Evaluation**: Design metrics and procedures to evaluate the performance of the MIMO configuration. This may include measuring parameters such as throughput, bit error rate (BER), and spectral efficiency.


7. **Optimization and Analysis**: Identify the best parameters and settings for specific application.


8. **Visualization**: Develop visualization tools to help you visualize the behavior of your MIMO simulation. This can be useful for understanding the dynamics of the system and identifying potential problems.


9. **Extend to Multiple Antennas**: Massive MIMO systems.


10. **Simulate Different Scenarios**: Different antenna configurations, different propagation environments, and different traffic patterns. This will provide a more comprehensive understanding of the performance of MIMO systems in different conditions.

## 5G simulations
### QAM over AWGN channel
{:center-img: style="text-align: center;"}
![QAM over AWGN](/images/awgn_channel_transmission.png){: width="90%" title="QAM transmission over an AWGN channel"}
{:center-img}

### Rust code of QAM

{% highlight rust %}
pub fn qam(num_bits_per_symbol: usize, normalize: bool) -> Vec<Complex<f32>> {
    // Check if num_bits_per_symbol is even and greater than zero
    assert!(
        num_bits_per_symbol % 2 == 0,
        "num_bits_per_symbol must be a multiple of 2"
    );
    assert!(
        num_bits_per_symbol > 0,
        "num_bits_per_symbol must be greater than zero"
    );

    // Build constellation by iterating through all points
    let mut c = Vec::with_capacity(2usize.pow(num_bits_per_symbol as u32));
    for i in 0..2usize.pow(num_bits_per_symbol as u32) {
        let b: Vec<_> = format!("{:0width$b}", i, width = num_bits_per_symbol)
            .chars()
            .map(|c| c.to_digit(10).unwrap() as i32)
            .collect();

        let real_part = pam_gray(
            &b[0..num_bits_per_symbol]
                .iter()
                .cloned()
                .step_by(2)
                .collect::<Vec<_>>(),
        );
        let imag_part = pam_gray(
            &b[1..num_bits_per_symbol]
                .iter()
                .cloned()
                .step_by(2)
                .collect::<Vec<_>>(),
        );

        c.push(Complex::new(real_part as f32, imag_part as f32));
    }

    if normalize {
        // Normalize to unit energy
        let n = num_bits_per_symbol / 2;
        let n1 = n as isize;
        let qam_var = (1..=2usize.pow(n as u32 - 1))
            .map(|i| (2 * i - 1).pow(2))
            .sum::<usize>() as f32
            / 2f32.powi((n1 - 2) as i32);
        c.iter_mut().for_each(|point| *point /= qam_var.sqrt());
    }

    c
}

{% endhighlight %}

* PAM gray labelling
{% highlight rust %}
/// Maps a bit vector to a PAM constellation points with Gray labeling.
pub fn pam_gray(b: &[i32]) -> i32 {
    if b.len() > 1 {
        return (1 - 2 * b[0]) * ((2_i32).pow(b.len() as u32 - 1) - pam_gray(&b[1..]));
    }
    1 - 2 * b[0]
}
{% endhighlight %}

### **✏️**...⏩
