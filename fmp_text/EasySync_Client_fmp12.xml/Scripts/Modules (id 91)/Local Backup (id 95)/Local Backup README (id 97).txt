#########################################
# Local Backup
#########################################
# https://github.com/jbante/FM-LocalBackup
# By Jeremy Bante
#
# This module is inspired by solutions by Kevin Frank (with help from Bruce Robertson) and Michael Rocharde.
# "A Simple Backup Script, revised" by Kevin Frank: http://www.filemakerhacks.com/?p=5293
# Concise Design (Bruce Robertson): http://www.concise-design.com
# "FileMaker & Me" by Michael Rocharde: http://itunes.apple.com/us/book/filemaker-me/id532231582?mt=11
#
#
#########################################
# Introduction
#########################################
# Local Backup creates backup copies of non-hosted solutions during development.
# Since some developers prefer to work on files locally, not hosted on a server, they miss out on the backup features of FileMaker Server. This module gives developers a substitute backup mechanism.
#
#
#########################################
# Usage
#########################################
# To create a local backup right now, run the "Create Local Backup of All Solution Files" script.
# To start making local backups automatically every 10 minutes, run the "Start Auto Backup" script. The backup interval can be changed by editing the "Get Local Backup Settings" script.
# To stop making local backup automatically, just close the auto-backup window, which will stop the OnTimer trigger from firing.
#
#
#########################################
# Installation
#########################################
# As a best practice, I recommend choosing one file to act as your solution's "dispatch" file. Then steps 2-N only have to be performed in the dispatch file.
# 1. Copy the "Local Backup" script folder into the "Modules" folder of each file in your solution.
# 2. In each non-dispatch file, edit the "Create Local Backup of All Solution Files" script to call the "Dispatch Backup of All Solution Files" script from the dispatch file.
# 3. In the dispatch file, edit the "Create Local Backup of Solution File ..." script to reference each file in your solution.
# 4. In the dispatch file, edit the "Go to Auto Backup Layout" script to specify a layout in your solution to use as the Auto Backup splashscreen. Auto Backups use a dedicated window with an OnTimer trigger to run repeated backups without interfering with any OnTimer triggers you may be using with other windows. This layout specifies what to display in that window.
# 5. (optional) In the dispatch file, edit the "Get Local Backup Settings" script to use a non-default backup path, auto-backup interval, auto-backup window name, or auto-backup window position.
#
#
#########################################
# Configuration Options
#########################################
# By default, Local Backup saves the backup copies of files to a timestamped folder within a "Backup" folder within the same directory as the solution files.
# Developers can choose to save to a different location by modifying the "Get Local Backup Settings" script to return a different backupFolderPath result.
#
# By default, the auto backup runs every 10 minutes.
# Developers can choose a different OnTimer interval by modifying the "Get Local Backup Settings" script to return a different backupIntervalSeconds result.
# If you change the setting while auto-backup is active, the new interval takes effect at the end of the next backup.
#
# The auto-backup window name and initial position can be changed by editing the "Get Local Backup Settings" script.
#
#
#########################################
# License
#########################################
# Anyone may do anything with this software. There is no warranty.
#
#
#########################################


---
Script:
  includeInMenu: 'False'
  runFullAccess: 'False'
  id: '97'
  name: 'Local Backup: README'
  StepList:
    Step:
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#########################################'
      Text: '########################################'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# Local Backup'
      Text: ' Local Backup'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#########################################'
      Text: '########################################'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# https://github.com/jbante/FM-LocalBackup'
      Text: ' https://github.com/jbante/FM-LocalBackup'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# By Jeremy Bante'
      Text: ' By Jeremy Bante'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# This module is inspired by solutions by Kevin Frank (with help
        from Bruce Robertson) and Michael Rocharde.'
      Text: ' This module is inspired by solutions by Kevin Frank (with help from
        Bruce Robertson) and Michael Rocharde.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# "A Simple Backup Script, revised" by Kevin Frank: http://www.filemakerhacks.com/?p=5293'
      Text: ' "A Simple Backup Script, revised" by Kevin Frank: http://www.filemakerhacks.com/?p=5293'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# Concise Design (Bruce Robertson): http://www.concise-design.com'
      Text: ' Concise Design (Bruce Robertson): http://www.concise-design.com'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# "FileMaker & Me" by Michael Rocharde: http://itunes.apple.com/us/book/filemaker-me/id532231582?mt=11'
      Text: ' "FileMaker & Me" by Michael Rocharde: http://itunes.apple.com/us/book/filemaker-me/id532231582?mt=11'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#########################################'
      Text: '########################################'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# Introduction'
      Text: ' Introduction'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#########################################'
      Text: '########################################'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# Local Backup creates backup copies of non-hosted solutions during
        development.'
      Text: ' Local Backup creates backup copies of non-hosted solutions during development.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# Since some developers prefer to work on files locally, not hosted
        on a server, they miss out on the backup features of FileMaker Server. This
        module gives developers a substitute backup mechanism.'
      Text: ' Since some developers prefer to work on files locally, not hosted on
        a server, they miss out on the backup features of FileMaker Server. This module
        gives developers a substitute backup mechanism.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#########################################'
      Text: '########################################'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# Usage'
      Text: ' Usage'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#########################################'
      Text: '########################################'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# To create a local backup right now, run the "Create Local Backup
        of All Solution Files" script.'
      Text: ' To create a local backup right now, run the "Create Local Backup of
        All Solution Files" script.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# To start making local backups automatically every 10 minutes, run
        the "Start Auto Backup" script. The backup interval can be changed by editing
        the "Get Local Backup Settings" script.'
      Text: ' To start making local backups automatically every 10 minutes, run the
        "Start Auto Backup" script. The backup interval can be changed by editing
        the "Get Local Backup Settings" script.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# To stop making local backup automatically, just close the auto-backup
        window, which will stop the OnTimer trigger from firing.'
      Text: ' To stop making local backup automatically, just close the auto-backup
        window, which will stop the OnTimer trigger from firing.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#########################################'
      Text: '########################################'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# Installation'
      Text: ' Installation'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#########################################'
      Text: '########################################'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# As a best practice, I recommend choosing one file to act as your
        solution''s "dispatch" file. Then steps 2-N only have to be performed in the
        dispatch file.'
      Text: ' As a best practice, I recommend choosing one file to act as your solution''s
        "dispatch" file. Then steps 2-N only have to be performed in the dispatch
        file.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# 1. Copy the "Local Backup" script folder into the "Modules" folder
        of each file in your solution.'
      Text: ' 1. Copy the "Local Backup" script folder into the "Modules" folder of
        each file in your solution.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# 2. In each non-dispatch file, edit the "Create Local Backup of
        All Solution Files" script to call the "Dispatch Backup of All Solution Files"
        script from the dispatch file.'
      Text: ' 2. In each non-dispatch file, edit the "Create Local Backup of All Solution
        Files" script to call the "Dispatch Backup of All Solution Files" script from
        the dispatch file.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# 3. In the dispatch file, edit the "Create Local Backup of Solution
        File ..." script to reference each file in your solution.'
      Text: ' 3. In the dispatch file, edit the "Create Local Backup of Solution File
        ..." script to reference each file in your solution.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# 4. In the dispatch file, edit the "Go to Auto Backup Layout" script
        to specify a layout in your solution to use as the Auto Backup splashscreen.
        Auto Backups use a dedicated window with an OnTimer trigger to run repeated
        backups without interfering with any OnTimer triggers you may be using with
        other windows. This layout specifies what to display in that window.'
      Text: ' 4. In the dispatch file, edit the "Go to Auto Backup Layout" script
        to specify a layout in your solution to use as the Auto Backup splashscreen.
        Auto Backups use a dedicated window with an OnTimer trigger to run repeated
        backups without interfering with any OnTimer triggers you may be using with
        other windows. This layout specifies what to display in that window.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# 5. (optional) In the dispatch file, edit the "Get Local Backup
        Settings" script to use a non-default backup path, auto-backup interval, auto-backup
        window name, or auto-backup window position.'
      Text: ' 5. (optional) In the dispatch file, edit the "Get Local Backup Settings"
        script to use a non-default backup path, auto-backup interval, auto-backup
        window name, or auto-backup window position.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#########################################'
      Text: '########################################'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# Configuration Options'
      Text: ' Configuration Options'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#########################################'
      Text: '########################################'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# By default, Local Backup saves the backup copies of files to a
        timestamped folder within a "Backup" folder within the same directory as the
        solution files.'
      Text: ' By default, Local Backup saves the backup copies of files to a timestamped
        folder within a "Backup" folder within the same directory as the solution
        files.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# Developers can choose to save to a different location by modifying
        the "Get Local Backup Settings" script to return a different backupFolderPath
        result.'
      Text: ' Developers can choose to save to a different location by modifying the
        "Get Local Backup Settings" script to return a different backupFolderPath
        result.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# By default, the auto backup runs every 10 minutes.'
      Text: ' By default, the auto backup runs every 10 minutes.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# Developers can choose a different OnTimer interval by modifying
        the "Get Local Backup Settings" script to return a different backupIntervalSeconds
        result.'
      Text: ' Developers can choose a different OnTimer interval by modifying the
        "Get Local Backup Settings" script to return a different backupIntervalSeconds
        result.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# If you change the setting while auto-backup is active, the new
        interval takes effect at the end of the next backup.'
      Text: ' If you change the setting while auto-backup is active, the new interval
        takes effect at the end of the next backup.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# The auto-backup window name and initial position can be changed
        by editing the "Get Local Backup Settings" script.'
      Text: ' The auto-backup window name and initial position can be changed by editing
        the "Get Local Backup Settings" script.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#########################################'
      Text: '########################################'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# License'
      Text: ' License'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#########################################'
      Text: '########################################'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '# Anyone may do anything with this software. There is no warranty.'
      Text: ' Anyone may do anything with this software. There is no warranty.'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#'
    - enable: 'True'
      id: '89'
      name: Comment
      StepText: '#########################################'
      Text: '########################################'
