# KUBECTL EXEC:

kubectl exec $POD_NAME -- ls -la /
kubectl exec $POD_NAME bash (/bin/bash or sh)

# DOCKER EXEC:
docker exec -it $CONTAINER /bin/bash
docker exec $CONTAINER ls <dir path>

docker run -d -p 22 $IMAGE /usr/sbin/sshd -D

# NSENTER:
PID=$(docker inspect --format {{.State.Pid}} <container_name_or_ID>)
nsenter --target $PID --mount --uts --ipc --net --pid

# containerd
NAME:
   ctr containers exec - exec another process in an existing container

USAGE:
   ctr containers exec [command options] [arguments...]

OPTIONS:
   --id                                         container id to add the process to
   --pid                                        process id for the new process
   --attach, -a                                 connect to the stdio of the container
   --cwd                                        current working directory for the process
   --tty, -t                                    create a terminal for the process
   --env, -e [--env option --env option]        environment variables for the process
   --uid, -u "0"                                user id of the user for the process
   --gid, -g "0"                                group id of the user for the process

# SSH
ssh -L LOCALPORT:localhost:REMOTEPORT <REMOTE IP>
# ex: ssh -L 1313:localhost:1313 192.168.1.250

# Deploy a priv daemon set https://raesene.github.io/blog/2019/04/01/The-most-pointless-kubernetes-command-ever/
curl -L jimsurls.com/yaml/root-daemon.yaml > kubectl apply -f -
kubectl exec -it noderootpod chroot /host