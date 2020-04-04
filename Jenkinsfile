pipeline {
   def approvaMap
   agent any
   stages {
      stage ('pre deploy') {
         steps {
            script {
               approvaMap = input (
                  message: '准备发布到什么环境？',
                  ok: '确认',
                  parameters: [
                     choice (choices: ['dev\\ntete\\nprod'], description: '发布到什么环境？', name: 'ENV'),
                     string (defaultValue: '', description: '', name: 'myparam', trim: false)
                  ],
                  submitter: 'admin,admin2,releaseGropup'
                  submitterParameter: 'APPROVER'
               )
            }
         }
      }
      stage ('deploy') {
         steps {
            echo "发布作者是：${approvaMap['APPROVER']}"
            echo "发布的环境是：${approvaMap['ENV']}"
            echo "自定义参数是：${approvaMap['myparam']}"
         }
      }
   }
}