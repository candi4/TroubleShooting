# tensorboard_plot
Issues when plotting graphs with tensorboard

## Plot multiple fils in one graph
```shell
tensorboard --logdir_spec=name1:PPO_3,name2:PPO_4
tensorboard --logdir ./a2c_cartpole_tensorboard/;./ppo2_cartpole_tensorboard/
```

## View tensorboard used in server
```
# In local
ssh -N -L 6006:localhost:6006 user@server_ip
```
* The first 6006 is the local port on your machine. Use this number for `http://localhost:6006` in local.
* The second 6006 is the remote port on the server where TensorBoard is running.