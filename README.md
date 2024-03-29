# Stats

Quickly create random variables for common distributions and export to csv or json.

## Installation

`pip3 install .`

## Example

Using random variables as arguments and in equations:

`stats random -i "x ~ poisson(2); y ~ exp(x); z = x * y;" --output csv --nreps 10 --decimals 3`

```
x,y,z
2,3.964,7.927
1,1.709,1.709
2,0.322,0.644
3,4.033,12.098
2,3.485,6.971
2,3.141,6.283
0,0.0,0.0
0,0.0,0.0
1,0.045,0.045
4,2.617,10.469
```

Piping to plot: 

```
stats random -i "x ~ norm(15, 3); y ~ norm(10, 1); z = x * y;" --output csv --nreps 1000 --decimals 3 
   | tail -n+2 
   | awk -F "," '{print $3}' 
   | feedgnuplot --histogram 0 --binwidth 15
```
![plot](https://github.com/natefduncan/random-vars/assets/30030731/ecfda49f-a469-466d-8770-0c77262196e4)

From file:

```
stats random -f examples/roi.example | tail -n+2 | awk -F "," '{print $NF}' | feedgnuplot --histogram 0 --binwidth 10000
```
![image](https://github.com/natefduncan/stats/assets/30030731/efb5c842-48ee-4e46-8c4d-72eb14f33b2b)

