# Google-drive-folders-list

🌟 Streamline Your Google Drive with this Simple Script! 🚀

Are you grappling with a cluttered Google Drive? Discover a game-changing script that automatically lists all your Google Drive folders and their links in a Google Sheet. Ideal for educators, project managers, or anyone juggling numerous folders!

🔍 What This Script Does:

Begins with a specified main folder in your Google Drive.
Recursively traverses all its subfolders.
Neatly catalogs each folder’s name and its direct link in a Google Sheet.
🛠️ Detailed Script Breakdown:

function listAllSubfolders() {
var mainFolderId = ‘YOUR_FOLDER_ID’; // Replace with your main folder’s ID
var mainFolder = DriveApp.getFolderById(mainFolderId);
var data = [];
var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
sheet.clear();
sheet.getRange(‘A1’).setValue(‘Listing all subfolders…’);

function getAllSubfolders(folder, depth) {
var subFolders = folder.getFolders();
while (subFolders.hasNext()) {
var subFolder = subFolders.next();
var prefix = ‘>’.repeat(depth); // Adds indentation for hierarchy
data.push([prefix + subFolder.getName(), subFolder.getUrl()]);
getAllSubfolders(subFolder, depth + 1);
}
}

getAllSubfolders(mainFolder, 0);
if (data.length > 0) {
sheet.getRange(2, 1, data.length, 2).setValues(data); // Populates the sheet
} else {
sheet.getRange(‘A1’).setValue(‘No subfolders found’);
}
sheet.getRange(‘B1’).setValue(‘Complete’);
}

📌 Easy Steps for Usage:

Identify Your Folder ID:
Open the desired folder in Google Drive.
The URL will be drive.google.com/drive/folders/YOUR_FOLDER_ID.
Copy the YOUR_FOLDER_ID part.
Script Setup:
Launch a new Google Sheet.
Navigate to Extensions > Apps Script.
Clear existing code and paste the provided script.
Substitute 'YOUR_FOLDER_ID' in the script with your actual folder ID.
Execute the Script:
Save via the disk icon, then run with the play button.
Grant necessary permissions if asked.
Your Google Sheet will then start filling up with folder names and links!
🎉 Key Advantages:

Effortlessly organizes and tracks folders.
Generates a tidy, accessible directory of your Google Drive folders.
Adaptable for various applications.
📢 Help others achieve digital neatness! This script is a step towards enhancing productivity and order!

#GoogleDriveTips #ProductivityTools #TechHacks #GoogleAppsScript #OrganizeYourLife


# Google Drive Folder Lister

This repository contains a Google Apps Script that helps users list all subfolders from a specified Google Drive folder into a Google Sheet. It's particularly useful for managing large numbers of folders and maintaining an organized directory.

## Features
- Lists all subfolders and their URLs in a structured format.
- Works with deeply nested folder structures.
- Customizable to suit specific needs.

## How to Use
1. **Set Up Google Sheets:**
   - Open a new Google Sheet.
   - Go to `Extensions > Apps Script`.
   - Replace any existing content with the script from `FolderLister.gs`.

2. **Run the Script:**
   - Save and run the script within the Apps Script editor.
   - Authorize the script if prompted.

3. **View Results:**
   - Return to your Google Sheet to see a hierarchical list of all subfolders.

## Customization
You can customize the script by modifying the source code in `FolderLister.gs`. For example, you can change the starting folder or adjust the output format.

## Contributions
Contributions to this project are welcome. Feel free to fork the repository and submit pull requests.

## License
This project is licensed under the [MIT License](LICENSE).

## Disclaimer
This script is provided "as is," and users should use it at their own risk. We are not responsible for any loss of data or other issues that may arise from using this script.


