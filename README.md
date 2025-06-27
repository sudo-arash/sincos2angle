# [sin, cos] => angle
Convert sin and cos to an angle using neural networks in MATLAB.

## How to use
First, load the network using this command:
```matlab
load("network.mat");
```
Then, you need to give it sin and cos of the angle you want! But, you have to first convert angle to radians:
```matlab
angle = 30;
inputs = [sin(deg2rad(angle)), cos(dregrad(angle))];
```
And now, we use the `net` function:
```matlab
net(inputs)
```

## Training
We had a dataset of about 10,000 inputs and outputs which were like this:
```matlab
outputs = linspace(0, 359, 10000); % We didn't train the network to do 360 degree or negative degrees.
inputs = [sin(deg2rad(a)), cos(dregrad(a))];
% and then we setup the network and used the train function to train it.
train(net, inputs, outputs);
```

## Layers
We first thought one hidden layer does the job, but it still failed the validation tests. So, we changed it to 2. The first layer has about 15 neurons while the second has 10. This gave better results.

## Limitations
You can give it negative angles or angles bigger than 359. This is because of the fact that we couldn't train the network to learn 0 or 360 degrees, that would change it's behaviour completely.
