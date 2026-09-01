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