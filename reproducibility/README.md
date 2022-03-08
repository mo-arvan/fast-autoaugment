```bash
export PROJECT_NAME=fast-autoaugment

docker build -t ${PROJECT_NAME}_image -f reproducibility/dockerfile .


docker run --rm --ipc=host --gpus all -v ${PWD}:/workspace -it ${PROJECT_NAME}_image bash

# inside the container


# Download the dataset, instructions are included in the main readme file.

export PYTHONPATH=$PYTHONPATH:$PWD
python FastAutoAugment/train.py -c confs/wresnet40x2_cifar.yaml --aug fa_reduced_cifar10 --dataset cifar10
```

