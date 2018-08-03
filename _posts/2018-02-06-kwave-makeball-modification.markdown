---
layout: post
title:  "How to make an arbitrary scattering ball phantom in k-Wave ultrasound toolbox!"
date:   2018-02-06 15:45:00 +0100
categories: projects
math: false
---

## About k-Wave ultrasound simulation toolbox

[k-Wave](https://www.k-wave.org) is an open source acoustics toolbox for MATLAB and C++. It is a time-domain acoustic model, based on the *k*-space pseudo-spectral method, for complex and tissue-realistic medium.

## Something about computational efficiency

The simulation functions are both fast and easy to use. However, to simulation complex scenarios, especially for higher frequency propagation, even the `C` functions are slow, e.g., almost 24 hours is needed to simulate a single medical B-mode image. So, a powerful single or double GPU, like [`GeForce GTX TITAN Z`](https://www.nvidia.com/gtx-700-graphics-cards/gtx-titan-z/) is preferred. 

### "makeBall.m" need to be modified

`makeBall.m` creates a binary map of a filled ball within a 3D grid. It was found that it can only be used when `dx=dy=dz`, so to create an arbetrary ball, the following codes can be used:

* Since the coordinate origin is in the center of the k-Wave grid matrix, but the locations of the scatters are relative to the upperleft corner of the grid. So, first, set the scatter position:

{% highlight Matlab %}
% define a sphere for a highly scattering region
radius = 2e-3;      % [m]
x_pos = 20e-3;      % [m]
y_pos = 12.8e-3;    % [m]
{% endhighlight %}

* Then construct a boolean array setting `True` at the voxels where the scatters are located: 

{% highlight Matlab %}
sound_speed_map = c0 * ones(Nx_tot, Ny_tot, Nz_tot) .* background_map;
density_map = rho0 * ones(Nx_tot, Ny_tot, Nz_tot) .* background_map;
        
% define a sphere for a highly scattering region
scattering_region1 = zeros(size(density_map));
[y_pos_tot, x_pos_tot, z_pos_tot] = meshgrid( (0:Ny_tot-1)*dy, kgrid.x_vec
	-kgrid.x_vec(1), kgrid.z_vec);
scattering_region1( (x_pos_tot- x_pos).^2 + (y_pos_tot- y_pos).^2 + (z_pos_tot
	- delta_z(ifrm)).^2 <= radius^2) = 1;
% assign region
sound_speed_map(scattering_region1 == 1) = scattering_c0(scattering_region1 ==1);
density_map(scattering_region1 == 1) = scattering_rho0(scattering_region1 == 1);
{% endhighlight %}

* Other parameters refer to the k-Wave example code [Ultrasound B-mode simulation](http://www.k-wave.org/documentation/example_us_bmode_linear_transducer.php).

One example phantom is as follows, here `dx = 0.1388mm`, `dy=dz = 0.15mm`:

{:center-img: style="text-align: center;"}
![phantom](/images/phantom.png){:height="418px" width="228px"}
{:center-img}

