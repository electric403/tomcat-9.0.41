node {
    checkout scm
    stage("BlackDuckSecruityScan") {
        if (env.BRANCH_NAME == 'main' || env.BRANCH_NAME =~ /^PR-\d+$/) {
            def status = security_scan product: 'blackducksca',
                // Uncomment if below parameters are not set in global configuration
                // blackducksca_url: 'BLACKDUCKSCA_URL',             
                // blackducksca_token: 'BLACKDUCKSCA_TOKEN',
                // blackducksca_waitForScan: false,    // Used to support the async mode
                // bitbucket_token: 'BITBUCKET_TOKEN', // Used for PR comment. Use github_token for GitHub or gitlab_token for GitLab
                // bitbucket_username:'BITBUCKET_USERNAME' // Used for bitbucket cloud pr comment if app password is set as bitbucket_token 
                // project_directory: "PROJECT_DIRECTORY",
               
                // Pull Request Comments
                blackducksca_prComment_enabled: true,

                // Fix pull request creation
                // blackducksca_fixpr_enabled: true,
                // blackducksca_fixpr_filter_severities : "CRITICAL, MEDIUM",
                // blackducksca_fixpr_maxCount: 1,
                // blackducksca_fixpr_useUpgradeGuidance: 'SHORT_TERM'

                // SARIF report generation
                blackducksca_reports_sarif_create: true,
               
                // Optional parameters
                // blackducksca_reports_sarif_file_path: 'SARIF_FILE_PATH',
                // blackducksca_reports_sarif_groupSCAIssues: true,
                // blackducksca_reports_sarif_severities: 'CRITICAL',

                // To enable the use of self-signed certificates
                // network_ssl_trustAll: true
                
                // Uncomment below to add arbitrary CL parameters
                // detect_search_depth: 1
                // detect_config_path: '/USER/application.properties'
                // detect_args: '--detect.diagnostic=true'
                
                // Mark build status if issues found
                mark_build_status: 'UNSTABLE'
            
            // Uncomment to add custom logic based on return status
            // if (status == 8) { unstable 'policy violation' }
            // else if (status != 0) { error 'plugin failure' }
        }
    }
}
