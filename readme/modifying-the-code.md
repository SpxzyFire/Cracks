---
description: Fifth Step
icon: code
---

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
