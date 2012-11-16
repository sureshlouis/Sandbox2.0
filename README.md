Sandbox2.0
==========How to get it working in a stage2 environment:

    Get a stage2( either a VM stage from Nimbus.paypal.com or physical stage2). Assuming your stage2 name is STAGE2XXXX for below documentation
    Deploy spartaserv component
        Copy latest green build id of spartaserv
        Use the above to fire a deploy on your stage using this jenkins deploy job
    Deploy sandboxspartaweb component
        Copy latest green build id from this build job
        Create a deploy job o deploy the above on your stage. You can use this deploy job as a template.
    Deploy sandboxserv and dependent component. Refer this page for component list.
    Register a new app with paypal access. Refer this page for steps to reister app. Ensure the return url is specific to the stage on which you are deploying . (i.e https://www.stage2xxxxx.qa.paypal.com:11664/webapps/sandbox/foo/access)
    Change the application.properties at /x/web/STAGE2XXXX/sandboxspartaweb/webapp/WEB-INF/classes/config/application.properties to update the following properties:
    application.ppaccess.client_id=<client_id as recieved in previous step>
    application.ppaccess.client_secret=<app id as recieved in previous step>
    Restart servers on stage2 machine
    cd /x/web/STAGE2XXXXX
    ./sandboxspartaweb/shutdown.sh
    ./spartaserv/shutdown.sh
    ./spartaserv/start.sh
    ./sandboxspartaweb/start.sh
