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

