@Library('pesg-sl') _

def dynamic_label = '' + Math.abs(new Random().nextLong())
//map of options
// {"command": "/p/hdk/pu_tu/prd/design_data_mobility_workflow/resiliotest_sbox/venv/bin/python /p/hdk/pu_tu/prd/design_data_mobility_workflow/resiliotest_sbox/src/bin/dm_common --op migrate --comp_type git_git --req_id 201 --mig_id 1", 
// "environment": {"HOME": "/nfs/site/home/gkhec", "SHELL": "/usr/intel/bin/tcsh"}, 

def config = [cloudName:"netbatchcloud",
            templateName:"nb1",
            label:"nb1",
            options:null,
            target:"zsc16_normal",
            qslot:"/ilabs/hec/fe",
            containerImage:null,
            logFile:"/nfs/site/disks/hec_mod_0001/pkeshari//log_1702633223DgiL6114",
            nodeWa:"/nfs/site/disks/hec_mod_0001/pkeshari/jenkins",
            templateClass:"SLES12&&4C&&8G",
            containerPlatform:null,
            javaLocation :"/usr/intel/pkgs/openjdk/11.0.10/bin/java",
            inheritFrom:"nb1",
            useHarbor:false,
            harborProject:null,
            harborImage:null,
            cloudName:"netbatchcloud",
            WorkerTimeout:900,
            RetentionTimeout:900,
            RawTicketCache:"dmhec:gkhec:9419f88a522b4269b08f62c69044deb3"
]

jenkinsNetbatch(config)


def jobOptions =[             
                '--class-reservation':'disk=80'                
                ]

jenkinsNBTaskTemplate(
    cloud: 'netbatchcloud',
    inheritFrom: 'nb1', //if you want to extend an existing label
    label: dynamic_label,
    //target: 'iil_normal',
    //nodeWa: '/nfs/iil/disks/dheerajk_wa_01/jenkinstests',
    //name: dynamic_label, // Reusing the label as a name makes sense as long as it's unique  
    //javaLocation: '/usr/intel/pkgs/openjdk/11.0.10/bin/java',
    jvmOptions: '-Xms4g -Xmx8g -Xverify:none -XX:-PrintGCDetails -Xss2m',
    options: jobOptions
) {
    node(dynamic_label) {
        stage("test"){
            sh 'echo hello'
            sh 'pwd'
            sh 'ls'
            //sh 'which java'
            sh 'java -version'
            sh 'ls'
        }
    }
}
        
