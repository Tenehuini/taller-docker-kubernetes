docker pull nicopaez/passwordapi-java:java8-alpine

java8-alpine: Pulling from nicopaez/passwordapi-java
8e3ba11ec2a2: Pull complete 
311ad0da4533: Pull complete 
391a6a6b3651: Pull complete 
cc2824e94232: Pull complete 
Digest: sha256:58124e67b934e5f6adf2c3d528296e79705241291011ea5762ee6633d6184ab1
Status: Downloaded newer image for nicopaez/passwordapi-java:java8-alpine
docker.io/nicopaez/passwordapi-java:java8-alpine


docker pull nicopaez/passwordapi-java:java8-fabric

java8-fabric: Pulling from nicopaez/passwordapi-java
8e3ba11ec2a2: Already exists 
badf8d054232: Pull complete 
d7d4b67fcf69: Pull complete 
3ed763dda7b4: Pull complete 
1bb0a6746cf8: Pull complete 
3454c3be30cf: Pull complete 
369c59cc4ad1: Pull complete 
fc3c80fa4974: Pull complete 
9f7c344fecb0: Pull complete 
Digest: sha256:5aa4a6be9ec512ed350d850d4d328590ced48ae2845103deca8d3db5b3789d95
Status: Downloaded newer image for nicopaez/passwordapi-java:java8-fabric
docker.io/nicopaez/passwordapi-java:java8-fabric


Since 8e3ba11ec2a2 was downloaded on the previous pull, now already exists and it is shared between the images



docker inspect nicopaez/passwordapi-java:java8-alpine

"Layers": [
                "sha256:73046094a9b835e443af1a9d736fcfc11a994107500e474d0abf399499ed280c",
                "sha256:298c3bb2664fb7f8514ecdde8b76c0ca95c7c7b82eaa326a7e9661e017488164",
                "sha256:8bc7bbcd76b68a51a3b70de9f19faed58f9c0795802dbff98de584b7e7eb9c22",
                "sha256:07f83dc33f640a098b67a7587dfc42f0e91f3b21aa08a7a02e613edca4901e22"
            ]


docker inspect nicopaez/passwordapi-java:java8-fabric

"Layers": [
                "sha256:73046094a9b835e443af1a9d736fcfc11a994107500e474d0abf399499ed280c",
                "sha256:7884dc8a73eb153770c61d327c027df411ea035bb2292a0a75373481a4b7fbd0",
                "sha256:717d137b16f996bf59af63c2abfd89b69faec166381549203c1439d6fdc6ddf2",
                "sha256:b85e653858e97c56eedb2e19e225c482cbad71fd54f90059c0da3c2dc58713cf",
                "sha256:f42a66141db68550a56f7b8c4cd9e2f0127d94accfe77e124f4b68999e9374b3",
                "sha256:ad275ed181794a5e37d0b3964e23ecedbd272a03ba26215f8d83de65e27436a3",
                "sha256:dd69ad62f09595f6c7ffa79438b9e7b3f0135a8d8d3e425c1bc37c8a70abc635",
                "sha256:8bef50a12deaffef57f54aaf2facddce8c04ea9253efe8afd33c44b7d0fc2f8e",
                "sha256:b4b541fa416f1d2f1d983b11c28cb1a91e3c09167cabb0cfd29fcdeb2239721c"
            ]

We see here with the inspect command that the first layer is shared between the two docker images: sha256:73046094a9b835e443af1a9d736fcfc11a994107500e474d0abf399499ed280c

