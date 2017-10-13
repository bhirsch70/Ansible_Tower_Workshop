Ansible Workshop Facilitator's Tips
=========================================

This guide is designed to help an facilitator create all of the tools/access required to host a hands-on workshop and offer up some tips to ensure the workshop runs smoothly.  These instructions can be broken down into several categories.

* Configuring the workshop lab environment
* Accessing student documentation and instructor decks
* Onsite logistics

## Configuring the workshop lab environment

   1. Follow [lightbulb AWS training provisioner guide](https://github.com/ansible/lightbulb/tree/master/tools/aws_lab_setup).
   2. A couple of modifications to these instructions are sometimes made in the field.
    - Disabling `email` tasks in the provisioner.  Although the `email` tasks can be useful if you want lab information to be sent directly to the student, instructors have found this can lead to students attempting pre-work which can cause issues during the workshop.  To accomplish this, simply add `email: no` to the extra_vars.yml file you will use during the playbook run.
    - Use generic user info for your students in `users.yml`.  This makes it easier to create XX accounts without knowing exactly who may be in the workshop.  It is common for to have several walk-ins the day of the workshop which will cause distractions and last minute lab environment builds.  This method eliminates those issues by enabling the instructor to pre-build several extra lab environments and assigning them to last minute students.  You're `users.yml` should look similar to this.
   ```
   users:
     - name: Student01
       username: student01
       email: youraddress@redhat.com
     - name: Student02
       username: student02
       email: youraddress@redhat.com
   ```
   4. Launch the lab build and monitor carefully.
   `ansible-playbook provision_lab.yml -e @extra_vars.yml -e users.yml`

## Accessing student documentation and slides

   ### Student Guide and Presentation Slides
   * A general student guide and instructor slides are already hosted at http://ansible-workshop.redhatgov.io . (NOTE:  This guide is evolving and newer workshops can be previewed at http:) //ansible.redhatgov.io . This version is currently being integrated with the Lightbulb project)
   * Here you will find complete student instructions for each exercise as well as the presentation decks under the __Resources__ drop down.
   * During the workshop, it is recommended that you have a second device or printed copy or both.  Previous workshops have demonstrated that unless you've memorized all of it, you'll likely need to refer to the guide, but your laptop will most likely be projecting the slide decks.  Some students will fall behind and you'll need to refer back to other exercises/slides without having to change the projection for the entire class.

   ### Student Lab information
   * After your lab build, you will find a file called `instructors_inventory.txt` located in the `lightbulb/tools/aws_lab_setup/` directory.  
   * Use [github gist](https://gist.github.com/) to upload that file. (Or post it to a site of your choosing as long as the students can see the info the day-of)
   * Use some type of of URL shortener (like tinyurl or goo.gl) to create a more consumable URL for the inventory file.

## Onsite logistics
   * Arrive at least 45 minutes early to the workshop location to ensure the setup is correct and solve common problems.
     - Projector not working, only VGA, only HDMI, no adapters, mic not working, etc.
     - No work space for the facilitator(s), i.e. no podium, no table for your laptop, no chairs
     - Lacking whiteboard and/or flipchart - You need somewhere to post the Student Guide URL, student inventory URL, WiFI details, etc.
   * Post workshop information on the whiteboard or flipchart
     - URL for the Student Guide
     - URL for the inventory
     - WiFi information
   * Assign all participants a `student##`.  Writing/printing out stickies or index cards with `studentXX` and placing them at each seat prior to the workshop's start is an easy way to do this.
