container_name=rt-tests
image_name=rt-tests


check:
	@[ "${label}" ] || ( echo "label is not set"; exit 1 )


build-docker: 
	cd ..; docker build -f rt-tests/Dockerfile -t $(image_name) . 

run-docker: check
	docker run --rm -it --name $(container_name) --cap-add=sys_nice --cap-add=ipc_lock --cap-add=sys_rawio --ulimit rtprio=99 --device-cgroup-rule='c 10:* rmw' -v /dev:/dev -v /tmp:/tmp -e label=${label} $(image_name) 

rm-docker:
	docker stop $(container_name) && docker rm $(container_name)

