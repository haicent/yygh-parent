pipeline {
  agent {
    node {
      label 'maven'
    }

  }
  stages {
    stage('拉取代码') {
      agent none
      steps {
        container('maven') {
          git(credentialsId: 'nas-gitlab', url: 'http://gitlab.yinbin.ink:30000/test/yygh-parent.git', branch: 'master', changelog: true, poll: false)
        }

      }
    }

    stage('项目编译') {
      agent none
      steps {
        container('maven') {
          sh 'mvn clean package -DskipTests=true '
        }

      }
    }

    stage('default-2') {
      parallel {
        stage('构建 hospital-manage 镜像') {
          agent none
          steps {
            container('maven') {
              sh '''export PN=hospital-manage
docker build -t $PN:latest -f $PN/Dockerfile $PN'''
            }

          }
        }

        stage('构建 server-gateway 镜像') {
          agent none
          steps {
            container('maven') {
              sh '''export PN=server-gateway
docker build -t $PN:latest -f $PN/Dockerfile $PN'''
            }

          }
        }

        stage('构建 service-cmn 镜像') {
          agent none
          steps {
            container('maven') {
              sh '''export PN=service-cmn
              cd service
docker build -t $PN:latest -f $PN/Dockerfile $PN'''
            }

          }
        }

        stage('构建 service-hosp 镜像') {
          agent none
          steps {
            container('maven') {
              sh '''export PN=service-hosp
              cd service
docker build -t $PN:latest -f $PN/Dockerfile $PN'''
            }

          }
        }

        stage('构建 service-order 镜像') {
          agent none
          steps {
            container('maven') {
              sh '''export PN=service-order
              cd service
docker build -t $PN:latest -f $PN/Dockerfile $PN'''
            }

          }
        }

        stage('构建 service-oss 镜像') {
          agent none
          steps {
            container('maven') {
              sh '''export PN=service-oss
              cd service
docker build -t $PN:latest -f $PN/Dockerfile $PN'''
            }

          }
        }

        stage('构建 service-sms 镜像') {
          agent none
          steps {
            container('maven') {
              sh '''export PN=service-sms
              cd service
docker build -t $PN:latest -f $PN/Dockerfile $PN'''
            }

          }
        }

        stage('构建 service-statistics 镜像') {
          agent none
          steps {
            container('maven') {
              sh '''export PN=service-statistics
              cd service
docker build -t $PN:latest -f $PN/Dockerfile $PN'''
            }

          }
        }

        stage('构建 service-task 镜像') {
          agent none
          steps {
            container('maven') {
              sh '''export PN=service-task
              cd service
docker build -t $PN:latest -f $PN/Dockerfile $PN'''
            }

          }
        }

        stage('构建 service-user 镜像') {
          agent none
          steps {
            container('maven') {
              sh '''export PN=service-user
              cd service
docker build -t $PN:latest -f $PN/Dockerfile $PN'''
            }

          }
        }

      }
    }

    stage('default-3') {
      parallel {
        stage('推送 hospital-manage 镜像') {
          agent none
          steps {
            container('maven') {
              withCredentials([usernamePassword(credentialsId : 'harbor-docker-registry' ,passwordVariable : 'DOCKER_REGISTY_PASSWD' ,usernameVariable : 'DOCKER_REGISTY_USER' ,)]) {
                sh '''export APP_NAME=hospital-manage

echo "$DOCKER_REGISTY_PASSWD" | docker login $REGISTRY -u "$DOCKER_REGISTY_USER" --password-stdin

docker tag $APP_NAME:latest $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER

docker push $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER'''
              }

            }

          }
        }

        stage('推送 server-gateway 镜像') {
          agent none
          steps {
            container('maven') {
              withCredentials([usernamePassword(credentialsId : 'harbor-docker-registry' ,passwordVariable : 'DOCKER_REGISTY_PASSWD' ,usernameVariable : 'DOCKER_REGISTY_USER' ,)]) {
                sh '''export APP_NAME=server-gateway

echo "$DOCKER_REGISTY_PASSWD" | docker login $REGISTRY -u "$DOCKER_REGISTY_USER" --password-stdin

docker tag $APP_NAME:latest $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER

docker push $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER'''
              }

            }

          }
        }

        stage('推送 service-cmn 镜像') {
          agent none
          steps {
            container('maven') {
              withCredentials([usernamePassword(credentialsId : 'harbor-docker-registry' ,passwordVariable : 'DOCKER_REGISTY_PASSWD' ,usernameVariable : 'DOCKER_REGISTY_USER' ,)]) {
                sh '''export APP_NAME=service-cmn

echo "$DOCKER_REGISTY_PASSWD" | docker login $REGISTRY -u "$DOCKER_REGISTY_USER" --password-stdin

docker tag $APP_NAME:latest $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER

docker push $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER'''
              }

            }

          }
        }

        stage('推送 service-hosp 镜像') {
          agent none
          steps {
            container('maven') {
              withCredentials([usernamePassword(credentialsId : 'harbor-docker-registry' ,passwordVariable : 'DOCKER_REGISTY_PASSWD' ,usernameVariable : 'DOCKER_REGISTY_USER' ,)]) {
                sh '''export APP_NAME=service-hosp

echo "$DOCKER_REGISTY_PASSWD" | docker login $REGISTRY -u "$DOCKER_REGISTY_USER" --password-stdin

docker tag $APP_NAME:latest $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER

docker push $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER'''
              }

            }

          }
        }

        stage('推送 service-order 镜像') {
          agent none
          steps {
            container('maven') {
              withCredentials([usernamePassword(credentialsId : 'harbor-docker-registry' ,passwordVariable : 'DOCKER_REGISTY_PASSWD' ,usernameVariable : 'DOCKER_REGISTY_USER' ,)]) {
                sh '''export APP_NAME=service-order

echo "$DOCKER_REGISTY_PASSWD" | docker login $REGISTRY -u "$DOCKER_REGISTY_USER" --password-stdin

docker tag $APP_NAME:latest $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER

docker push $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER'''
              }

            }

          }
        }

        stage('推送 service-oss 镜像') {
          agent none
          steps {
            container('maven') {
              withCredentials([usernamePassword(credentialsId : 'harbor-docker-registry' ,passwordVariable : 'DOCKER_REGISTY_PASSWD' ,usernameVariable : 'DOCKER_REGISTY_USER' ,)]) {
                sh '''export APP_NAME=service-oss

echo "$DOCKER_REGISTY_PASSWD" | docker login $REGISTRY -u "$DOCKER_REGISTY_USER" --password-stdin

docker tag $APP_NAME:latest $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER

docker push $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER'''
              }

            }

          }
        }

        stage('推送 service-sms 镜像') {
          agent none
          steps {
            container('maven') {
              withCredentials([usernamePassword(credentialsId : 'harbor-docker-registry' ,passwordVariable : 'DOCKER_REGISTY_PASSWD' ,usernameVariable : 'DOCKER_REGISTY_USER' ,)]) {
                sh '''export APP_NAME=service-sms

echo "$DOCKER_REGISTY_PASSWD" | docker login $REGISTRY -u "$DOCKER_REGISTY_USER" --password-stdin

docker tag $APP_NAME:latest $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER

docker push $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER'''
              }

            }

          }
        }

        stage('推送 service-statistics 镜像') {
          agent none
          steps {
            container('maven') {
              withCredentials([usernamePassword(credentialsId : 'harbor-docker-registry' ,passwordVariable : 'DOCKER_REGISTY_PASSWD' ,usernameVariable : 'DOCKER_REGISTY_USER' ,)]) {
                sh '''export APP_NAME=service-statistics

echo "$DOCKER_REGISTY_PASSWD" | docker login $REGISTRY -u "$DOCKER_REGISTY_USER" --password-stdin

docker tag $APP_NAME:latest $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER

docker push $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER'''
              }

            }

          }
        }

        stage('推送 service-task 镜像') {
          agent none
          steps {
            container('maven') {
              withCredentials([usernamePassword(credentialsId : 'harbor-docker-registry' ,passwordVariable : 'DOCKER_REGISTY_PASSWD' ,usernameVariable : 'DOCKER_REGISTY_USER' ,)]) {
                sh '''export APP_NAME=service-task

echo "$DOCKER_REGISTY_PASSWD" | docker login $REGISTRY -u "$DOCKER_REGISTY_USER" --password-stdin

docker tag $APP_NAME:latest $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER

docker push $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER'''
              }

            }

          }
        }

        stage('推送 service-user 镜像') {
          agent none
          steps {
            container('maven') {
              withCredentials([usernamePassword(credentialsId : 'harbor-docker-registry' ,passwordVariable : 'DOCKER_REGISTY_PASSWD' ,usernameVariable : 'DOCKER_REGISTY_USER' ,)]) {
                sh '''export APP_NAME=service-user

echo "$DOCKER_REGISTY_PASSWD" | docker login $REGISTRY -u "$DOCKER_REGISTY_USER" --password-stdin

docker tag $APP_NAME:latest $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER

docker push $REGISTRY/$DOCKERHUB_NAMESPACE/$APP_NAME:v$BUILD_NUMBER'''
              }

            }

          }
        }

      }
    }

    stage('default-4') {
      parallel {
        stage('部署 hospital-manage 到dev集群') {
          agent none
          steps {
            kubernetesDeploy(configs: 'hospital-manage/deploy/**', enableConfigSubstitution: true, kubeconfigId: "$KUBECONFIG_CREDENTIAL_ID")
          }
        }

        stage('部署 server-gateway 到dev集群') {
          agent none
          steps {
            kubernetesDeploy(configs: 'server-gateway/deploy/**', enableConfigSubstitution: true, kubeconfigId: "$KUBECONFIG_CREDENTIAL_ID")
          }
        }

        stage('部署 service-cmn 到dev集群') {
          agent none
          steps {
            kubernetesDeploy(configs: 'service/service-cmn/deploy/**', enableConfigSubstitution: true, kubeconfigId: "$KUBECONFIG_CREDENTIAL_ID")
          }
        }

        stage('部署 service-hosp 到dev集群') {
          agent none
          steps {
            kubernetesDeploy(configs: 'service/service-hosp/deploy/**', enableConfigSubstitution: true, kubeconfigId: "$KUBECONFIG_CREDENTIAL_ID")
          }
        }

        stage('部署 service-order 到dev集群') {
          agent none
          steps {
            kubernetesDeploy(configs: 'service/service-order/deploy/**', enableConfigSubstitution: true, kubeconfigId: "$KUBECONFIG_CREDENTIAL_ID")
          }
        }

        stage('部署 service-oss 到dev集群') {
          agent none
          steps {
            kubernetesDeploy(configs: 'service/service-oss/deploy/**', enableConfigSubstitution: true, kubeconfigId: "$KUBECONFIG_CREDENTIAL_ID")
          }
        }

        stage('部署 service-sms 到dev集群') {
          agent none
          steps {
            kubernetesDeploy(configs: 'service/service-sms/deploy/**', enableConfigSubstitution: true, kubeconfigId: "$KUBECONFIG_CREDENTIAL_ID")
          }
        }

        stage('部署 service-statistics 到dev集群') {
          agent none
          steps {
            kubernetesDeploy(configs: 'service/service-statistics/deploy/**', enableConfigSubstitution: true, kubeconfigId: "$KUBECONFIG_CREDENTIAL_ID")
          }
        }

        stage('部署 service-task 到dev集群') {
          agent none
          steps {
            kubernetesDeploy(configs: 'service/service-task/deploy/**', enableConfigSubstitution: true, kubeconfigId: "$KUBECONFIG_CREDENTIAL_ID")
          }
        }

        stage('部署 service-user 到dev集群') {
          agent none
          steps {
            kubernetesDeploy(configs: 'service/service-user/deploy/**', enableConfigSubstitution: true, kubeconfigId: "$KUBECONFIG_CREDENTIAL_ID")
          }
        }

      }
    }

    stage('ok') {
      agent none
      steps {
        echo 'ok!!!'
      }
    }

  }
  environment {
    DOCKER_CREDENTIAL_ID = 'dockerhub-id'
    GITHUB_CREDENTIAL_ID = 'github-id'
    KUBECONFIG_CREDENTIAL_ID = 'kubeconfig-dev-id'
    REGISTRY = '192.168.122.10:30002'
    DOCKERHUB_NAMESPACE = 'devops_syt'
    GITHUB_ACCOUNT = 'kubesphere'
    APP_NAME = 'devops-java-sample'
  }
}