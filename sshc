#!/bin/sh

unset command_builder
unset name

print_usage() {
  printf "Usage: sshc [SSH_SERVER] OR sshc -n SESSION_NAME -s SSH_SERVER\n"
}

while getopts 'n:s:' flag; do
  case "${flag}" in
    n) name="${OPTARG}"; command_builder="${command_builder} -S ${name}" ;;
    s) command_builder="${command_builder} -dm ssh ${OPTARG}" ;; 
    *) print_usage
       exit 1 ;;
  esac
done


if [ -z "$command_builder" ]
then
	if [ -z ${1} ]
	then
		print_usage
		exit
	else
		command_builder=" -S ${1} -dm ssh ${1}"
		name=${1}
	fi
fi

{
eval "screen${command_builder}"
sleep 0.01 
screen -r "${name}"
} || {
	print_usage
}
