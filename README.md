# Docker Stacks

[Stacks](https://github.com/State/stacks) it's an Aws CloudFormation stacks management tool.
It can generate templates, list, create, delete and update stacks.

To use the docker image

        -> % docker run -it --rm -v $(HOME)/.aws:/root/.aws:ro \
            quay.io/ukhomeofficedigital/stacks stacks --profile default --region eu-west-1 list

            ukhomeofficedigital-guestbook-elb        CREATE_COMPLETE
            ukhomeofficedigital-kubernetes-elb       CREATE_COMPLETE
            ukhomeofficedigital-coreos-compute       UPDATE_COMPLETE
            ukhomeofficedigital-coreos-etcd          UPDATE_COMPLETE
            ukhomeofficedigital-coreos-etcd-volumes  UPDATE_COMPLETE
            ukhomeofficedigital-infra                CREATE_COMPLETE


There are a few details you have to provide. AWS Credentials, profile and default region.
The name of your stack (called ENV) and the location of the templates folder.

        -> % docker run -it --rm
                -e AWS_PROFILE=HomeOfficeProfile \
                -e AWS_REGION=eu-west-1 \
                -e ENV=MyNewStack \
                -v $(HOME)/.aws:/root/.aws:ro  \
                -v $(pwd)/../examples/templates:/templates
            quay.io/ukhomeofficedigital/stacks \
                stacks -p $AWS_PROFILE -r $AWS_REGION create -e ${ENV} -t /templates/infra.yaml ${ENV}-infra

## Contributing

Feel free to submit pull requests and issues. If it's a particularly large PR, you may wish to
discuss it in an issue first.

Please note that this project is released with a
[Contributor Code of Conduct](https://github.com/UKHomeOffice/docker-stacks/blob/master/CODE_OF_CONDUCT.md).
By participating in this project you agree to abide by its terms.

## Versioning

We use [SemVer](http://semver.org/) for the version tags available See the tags on this repository.


## Authors

* **Ivan Pedrazas** - *Initial work* - [ipedrazas](https://github.com/ipedrazas)

See also the list of
[contributors](https://github.com/UKHomeOffice/docker-stacks/graphs/contributors) who participated
in this project.

## License

This project is licensed under the MIT License - see the
[LICENSE.md](https://github.com/UKHomeOffice/docker-stacks/blob/master/LICENSE.md) file for details
