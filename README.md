# onlineABM

This is an example of a basic online Attentional Bias Modification (ABM) experiment using Javascript and PHP. The experiment consists of a pre-training assessment, four daily trainig sessions, a post-training assessment, and follow-up design after one week.

To use it, you need to upload the unzipped directory to your website. I suggest getting hosting from Dreamhost - everything works with them (this isn't necessarily the case for all hosting providers, especially PHP functions). You will need a GMail account set up to automatically forward mails. You will also need a running cron job for emailing session-invitations, adjusted from the lines below:

  #!/bin/sh
  curl "https://www.myWebSite.com/2017_07_23_ABM/Online/mailsender.php?p=fakepassword46352"

The php script taskParams.php contains parameters you need to set up for the software to work on your system or to adjust the experiment. For instance, you will need to use the correct directory address and log-in details for your GMail.

Once uploaded, participants must follow a link to register. This would look soemthing like:

myWebSite.com/2017_07_23_ABM/Online/register.php?username=666&loginsrc=Nonsona

Replace the username "666" with the correct one. The login-source, loginsrc, can be set to Sona1 or Sona2 if you're integrating the experiment in Sona systems. The participant will be sent to an Information and Informed Consent screen where they can choose whether to participate and if so, fill in their email address and a time of day to receive invitations.

The first invitation will be sent immediately after registering. Most other invitations are sent one day after completing the previous session. The final invitation is sent after seven days.

---

The /Online directory contains the PHP functions. To understand the code, start with register.php and just follow the links, and when you test the experiment note the PHP pages you're sent to.

The /Online/jsfiles directory  contain directories with Javascript for questionnaires and tasks. Both questionnaires and tasks are controlled by a Manager function, which interfaces with the webpage and presents specific questionnaires and tasks in order.

The /Online/Stims directory contains subdirectories with pictures used for assessment and training. These can be changed as desired as long as the filenames remain the same, i.e., stim (1).jpg (and of course the number of stimuli are sufficient for the task; the provided Dot-Probe task needs 20 pictures per stimulus category).

Data are saved to the /Online/results directory. The data are saved as JSON strings, one line per questionnaire or trial.
