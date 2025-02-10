# Downloading DLL Spy

#### Steps to Install dnSpy and unzip

1. **Download dnSpy:** Visit the [official dnSpy GitHub page](https://github.com/dnSpy/dnSpy) to download the latest release.
2. **Extract the ZIP File:**
   * Locate the downloaded dnSpy ZIP file.
   * Right-click on the ZIP file and select 'Extract All' or use a tool like WinRAR or 7-Zip to unzip the contents.
3. **Run dnSpy:**
   * Navigate to the extracted folder.
   * Double-click on `dnSpy.exe` to launch the application.
4.  **Verify Installation:**

    * Ensure that dnSpy is running without errors.
    * Confirm all expected features are functioning as intended.

# Downloading Nezur Executor

Downloading Nezur from the right place is something everyone wants, as that you do not want to harm your computer

To install Nezur, follow these simple steps:

1. **Download Nezur**: Visit [Nezur's official download page](https://nezur.io/#downloads/) and download the latest version.
2. **Unzip the File**: Locate the downloaded ZIP file and unzip it using your preferred extraction tool.
3. **Copy to New Folder**: Once unzipped, copy the extracted files and paste them into a new folder on your computer for easy access.

# Finding the Correct Path

## Make sure you have added the DLL inside of dnSpy!

# How to add Nezur's DLL inside dnSpy

To add `Nezur_Interface.dll` in dnSpy, follow these steps:

1.  **Clear the Page:**

    Go to the top menu and click on **File**.

    Select **Close All** to clear any open files.
2. **Adding the DLL:**\
   Go to the top menu and click on **File**\
   Select **Open...** and select "Nezur\_Interface.dll"
3. **Adding the DLL (Second Method, more simple)**\
   Drag "Nezur\_Interface.dll" inside of the left bar of the DLL Spy\

once you have added the DLL, you are gonna need the path to get the Right code, here is how to find the path

1. **Finding the needed code's Path:**\
   Nezur\_Interface (1.0.0.0) \
   &#x20;  ├── Nezur\_Interface.dll\
   &#x20;        └── Nezur\_Interface\
   &#x20;               └── KeyPage\
   &#x20;                       └── Button\_Click

<figure><img src="../.gitbook/assets/Path.png" alt=""><figcaption><p>This is an exemple of the path</p></figcaption></figure>

# Modifying the Code

The Code in the "Button\_Click" Script should look like this

```cpp
// Nezur_Interface.KeyPage
// Token: 0x06000018 RID: 24 RVA: 0x00002564 File Offset: 0x00000764
[NullableContext(1)]
private void Button_Click(object sender, RoutedEventArgs e)
{
	string password = this.Key.Password;
	if (string.IsNullOrEmpty(password))
	{
		MessageBox.Show("License cannot be empty.");
		return;
	}
	KeyPage.KeyAuth.license(password);
	if (KeyPage.KeyAuth.response.success)
	{
		new MainWindow().Show();
		base.Close();
		return;
	}
	MessageBox.Show("Invalid license, please try again!");
}

```

If you read the code properly, you can see that the following script is the function when the code is correct

```cpp
		new MainWindow().Show();
		base.Close();
		return;
```

But yet, this is the code for what happens if you set the textbox of the Key to blank

```cpp
		MessageBox.Show("License cannot be empty.");
		return;
```

So, if you want to do so that instead of blocking, **it lets you threw**, you are going to want to take the first script and put it into the second, it should look something like this, in this case i will keep the **MessageBox** for more **User Quality,** you can **copy and paste** the following code

```cpp
// Nezur_Interface.KeyPage
// Token: 0x06000023 RID: 35 RVA: 0x00002D14 File Offset: 0x00000F14
[NullableContext(1)]
private void Button_Click(object sender, RoutedEventArgs e)
{
	string password = this.Key.Password;
	if (string.IsNullOrEmpty(password))
	{
		MessageBox.Show("Cracked by Zyren Hub");
		new MainWindow().Show();
		base.Close();
		return;
	}
	KeyPage.KeyAuth.license(password);
	if (KeyPage.KeyAuth.response.success)
	{
		new MainWindow().Show();
		base.Close();
		return;
	}
}

```

<figure><img src="../.gitbook/assets/image (3).png" alt="" width="297"><figcaption><p>When Clicked the Verify Key</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption><p>When clicked "Ok"</p></figcaption></figure>


# Finishing and Compiling

After you are done with the modification of the code, make sure that you Compile the file

Make sure you also disable anti virus because the DLL is falsely marked as a virus

# How it now works

Once you the DLL changed, you will still see the key system pop up, but in the code, if you read the code properly, you can see that it works only if you put nothing in the key it will let you threw, so make sure that you put nothing inside the textbox or else it will not work, there will also and obviously be a notification letting you know if it went threw

<figure><img src="../.gitbook/assets/image (1).png" alt="" width="300"><figcaption><p>In the Menu</p></figcaption></figure>
