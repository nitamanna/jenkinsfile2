pipeline {
	agent any
		stages {
			stage ('Stage one') {
				steps {
					echo "inside stage one"
				}
			}
			stage ('Stage two') {
				steps {
					input ('Do you want to proceed?')
				}
			}
			stage ('Stage three') {
				when {
					not {
						branch "master"
					}
					steps {
						echo "inside stage three"
					}
				}
			}
			stage ('Stage four') {
				parallel {
					stage ('Unit test') {
						steps {
							echo "Running the unit test from stage four"
						}
					}
					stage ('Integration test') {
						agent {
							docker {
								resourceNode true
								image 'ubuntu'
							}
						}
						steps {
							echo "Running the integration testing from stage four parallel"
						}
					}
				}
			}
		}
	}
