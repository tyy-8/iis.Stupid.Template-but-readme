# ii's Stupid Template
ii's Stupid Template is a mod menu template for Gorilla Tag with custom categories and the maximum amount of customization possible. This template is meant for more advanced users, so if you're a new menu creator, this could be difficult for you.

## Do I need permission to use this?
No, this template is free and public for anyone to use. You are welcome to utilize it for your projects, modify it to suit your needs, and share it with others. We believe in a collaborative and open community where resources are accessible to all.

---

# Installation

- Download the source code from [here](https://github.com/iiDk-the-actual/iis.Stupid.Template/releases/latest)
- Change your `<GamePath>` (Gorilla Tag directory) in `Directory.Build.props` if required
- Change the menu name in `PluginInfo.cs`
- Edit the menu visuals in `Menu/Settings.cs`
- Add buttons in `Menu/Buttons.cs`
- Build with `Ctrl` + `Shift` + `B`, it will get put in your plugins folder automatically

# Page Buttons
When in the project, to edit the page button position or scale, you need to go to `Menu/Main.cs`.

# Fixing Disconnect
To fix disconnect button at the top of the menu make this your `Classes/ButtonCollider.cs`

```
	internal class Button : MonoBehaviour
	{
		public string relatedText;

		public static float buttonCooldown = 0f;
		
		public void OnTriggerEnter(Collider collider)
		{
			if (relatedText == "Disconnect" && Time.time > buttonCooldown && collider == buttonCollider && menu != null)
			{
			
				if (Time.time > buttonCooldown && collider == buttonCollider && menu != null)
				{
					buttonCooldown = Time.time + 0.2f;
					GorillaTagger.Instance.StartVibration(rightHanded, GorillaTagger.Instance.tagHapticStrength / 2f, GorillaTagger.Instance.tagHapticDuration / 2f);
					GorillaTagger.Instance.offlineVRRig.PlayHandTapLocal(8, rightHanded, 0.4f);
					NetworkSystem.Instance.ReturnToSinglePlayer();
				}
			}
			else
			{
				if (Time.time > buttonCooldown && collider == buttonCollider && menu != null)
				{
					buttonCooldown = Time.time + 0.2f;
					GorillaTagger.Instance.StartVibration(rightHanded, GorillaTagger.Instance.tagHapticStrength / 2f, GorillaTagger.Instance.tagHapticDuration / 2f);
					GorillaTagger.Instance.offlineVRRig.PlayHandTapLocal(8, rightHanded, 0.4f);
					Toggle(this.relatedText);
				}
			}
		}
	}
```
