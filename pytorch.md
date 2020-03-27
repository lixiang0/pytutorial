#### ‘model.eval()’ vs ‘with torch.no_grad()’

- model.eval() will notify all your layers that you are in eval mode, that way, batchnorm or dropout layers will work in eval mode instead of training mode.
- torch.no_grad() impacts the autograd engine and deactivate it. It will reduce memory usage and speed up computations but you won’t be able to backprop (which you don’t want in an eval script).



#### What’s the difference between nn.ReLU() and nn.ReLU(inplace=True)?
inplace=True means that it will modify the input directly, without allocating any additional output. It can sometimes slightly decrease the memory usage, but may not always be a valid operation (because the original input is destroyed). However, if you don’t see an error, it means that your use case is valid.
