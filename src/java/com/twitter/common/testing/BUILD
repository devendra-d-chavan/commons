# ==================================================================================================
# Copyright 2011 Twitter, Inc.
# --------------------------------------------------------------------------------------------------
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this work except in compliance with the License.
# You may obtain a copy of the License in the LICENSE file, or at:
#
#  http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
# ==================================================================================================
from twitter.pants import artifact, globs, pants, java_library, jvm_binary

java_library(name = 'testing',
  dependencies = [
    '3rdparty:easymock',
    '3rdparty:guava',
    '3rdparty:junit',
    '3rdparty:tl4j',
  ],
  sources = [ 'EasyMockTest.java' ]
)

java_library(name = 'action',
  dependencies = [
    '3rdparty:guava',
    '3rdparty:tl4j',
    'src/java/com/twitter/common/application:action',
    'src/java/com/twitter/common/base',
  ],
  sources = [ 'TearDownRegistry.java' ]
)

java_library(name = 'junit-runner',
  provides = artifact(
    org = 'com.twitter.common',
    name = 'junit-runner',
    repo = 'build-support/commons/ivy:public',
  ),
  dependencies = [
    '3rdparty:args4j',
    '3rdparty:guava',
    '3rdparty:junit',
  ],
  sources = globs('runner/*.java')
).with_description("""
  A replacement for org.junit.runner.JUnitCore.main that adds:
  + support for running individual test methods using [classname]#[methodname]
  + support for stderr and stdout redirection for tests
  + support for ant style junit-report xml output
""")

jvm_binary(name = 'junit-runner-main',
  main = 'com.twitter.common.testing.runner.JUnitConsoleRunner',
  dependencies = [
    ':junit-runner',
  ]
)
