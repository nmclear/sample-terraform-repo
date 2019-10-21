# sample-terraform-repo

## Repository Structure
* examples/ - fully functional example of a module or stack.
    - alb/
    - microservice_infrastructure/
        - redis/
        - es/
        - kube2iam/
    - fargate_application/
        - service/
        -task/
* live/ - 100% matching the live AWS environment
    - apps/ - contains app-specific infratracture (a ec2 instance, database, es, redis)
        - microservices/
            - page-microservice/
                - dependencies.tf (include data object for vpc, sg, etc.)
                - redis/
                - es/
                - cloudwatch/
            - cover-microservice/
            - ink-microservice/
        - database_dr/
            - author_db/
            - words_db/
    - platform/ - contains all resources neccessary for a functional and secure platform
        - network
            - vpc/
            - lb/
        - compute
            eks/
            ecs/
* modules/ - shareable building blocks for live environment
    - tests/ -tests for modules
    - modules/
        - compute/
        - data/
        - network/
        - util/
        - stacks/ - larger modules made up of smaller modules
            - microservice/
            - fargate_application/
* tests/ - collection of tests every tf apply must pass
    - required_tests.go
    - deployed_to_vpc.go
    - tf_linting.go
