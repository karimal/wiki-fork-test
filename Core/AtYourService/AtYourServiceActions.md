### Action files
* Manages the lifecycle of service

* 2 supported formats .py & (.lua) ```coming soon```

* Example:
 ```shell
class Actions(ActionsBase):
    """
    implement methods of this class to change behaviour of lifecycle management of ays
    """
    def prepare(self,**args):
         """
         this gets executed before the files are downloaded & installed on approprate spots
         """
         return True

    def configure(self,**args):
         """
         this gets executed when files are installed
         this step is used to do configuration steps to the platform
         after this step the system will try to start the ays if anything needs to be started
         """
         return True

    def start(self,**args):
         """
         start happens because of info from main.hrd file but we can overrule this
         make sure to also call ActionBase.start(**args) in your implementation otherwise the default behaviour will not happen
         """
         return True

    def stop(self,**args):
         """
         if you want a gracefull shutdown implement this method
         a uptime check will be done afterwards (local)
         return True if stop was ok, if not this step will have failed & halt will be executed.
         """
         return True

    def halt(self,**args):
         """
         hard kill the app, std a linux kill is used, you can use this method to do something next to the std behaviour
         """
         return True

     def build(self,**args):
         """
         build instructions for the ays, make sure the builded ays ends up in right directory, this means where otherwise binaries would run from
         """
         pass

    def package(self,**args):
         """
         copy the files from the production location on the filesystem to the appropriate binary git repo
         """
         pass

    def check_up_local(self,**args):
         """
         do checks to see if process(es) is (are) running.
         this happens on system where process is
         """
         return True

    def check_down_local(self,**args):
         """
         do checks to see if process(es) are all down
         this happens on system where process is
         return True when down
         """
         return True

    def check_requirements(self,**args):
         """
         do checks if requirements are met to install this app
         e.g. can we connect to database, is this the right platform, ...
         """
         return True

    def monitor_local(self,**args):
         """
         do checks to see if all is ok locally to do with this package
         this happens on system where process is
         """
         return True

    def monitor_remote(self,**args):
         """
         do checks to see if all is ok from remote to do with this package
         this happens on system from which we install or monitor (unless if defined otherwise in hrd)
         """
         return True

    def cleanup(self,**args):
         """
         regular cleanup of env e.g. remove logfiles, ...
         is just to keep the system healthy
         """
         return True

    def data_export(self,**args):
         """
         export data of app to a central location (configured in hrd under whatever chosen params)
         return the location where to restore from (so that the restore action knows how to restore)
         we remember in $name.export the backed up events (epoch,$id,$state,$location)  $state is OK or ERROR
         """
         return False

    def data_import(self,id,**args):
         """
         import data of app to local location
         if specifies which retore to do, id corresponds with line item in the $name.export file
         """
         return False

    def uninstall(self,**args):
         """
         uninstall the apps, remove relevant files
         """
         pass

    def removedata(self,**args):
         """
         remove all data from the app (called when doing a reset)
         """
         pass

    def uninstall(self,**args):
         """
         uninstall the apps, remove relevant files
         """
         pass

    def upload(self,serviceobj,source,dest):
        """
        on central side only
        push service instance configuration to remote location
        """

    def download(self,serviceobj,source,dest):
        """
        on central side only
        pull service instance configuration from remote location
        """

    def executeaction(self,serviceobj,actionname):
        """
        on central side only
        remotly execute something in the service instance
        """
```
