# Termius-cracked by #beaubhavik

## Crack method

Install npm install asar
```shell
npm install -g asar
```
### for Windows

1. Unpack app.asar
```shell
cd C:\Users\beaud\AppData\Local\Programs\Termius\resources\
asar extract app.asar ./app  # No need to repackage after modification
mv app.asar app.asar.bak  # Keep a backup, or directly
rm app-update.yml  # Prevent automatic updates

```
2. Modify app/js/background-process.js

search `await this.api.bulkAccount`

`const e=await this.api.bulkAccount();` -> `var e=await this.api.bulkAccount();`

```
async updateUserProfile() {
            var e = await this.api.bulkAccount();
            e.account.pro_mode = true;
            e.account.need_to_update_subscription = false;
            e.account.current_period = {
                "from": "2022-01-01T00:00:00",
                "until": "2099-01-01T00:00:00"
            };
            e.account.plan_type = "Premium";
            e.account.user_type = "Premium";
            e.student = null;
            e.trial = null;
            e.account.authorized_features.show_trial_section = false;
            e.account.authorized_features.show_subscription_section = true;
            e.account.authorized_features.show_github_account_section = false;
            e.account.expired_screen_type = null;
            e.personal_subscription = {
                "now": new Date().toISOString().slice(0, -5),
                "status": "SUCCESS",
                "platform": "stripe",
                "current_period": {
                    "from": "2022-01-01T00:00:00",
                    "until": "2099-01-01T00:00:00"
                },
                "revokable": true,
                "refunded": false,
                "cancelable": true,
                "reactivatable": false,
                "currency": "usd",
                "created_at": "2022-01-01T00:00:00",
                "updated_at": new Date().toISOString().slice(0, -5),
                "valid_until": "2099-01-01T00:00:00",
                "auto_renew": true,
                "price": 12.0,
                "verbose_plan_name": "Termius Pro Monthly",
                "plan_type": "SINGLE",
                "is_expired": false
            };
            e.access_objects = [{
                "period": {
                    "start": "2022-01-01T00:00:00",
                    "end": "2099-01-01T00:00:00"
                },
                "title": "Cracked by #beaubhavik"
            }]

            return await this.setUserProfile(e), e
}
```
3. Enter below command in windows powershell (Replace path of your Termius.ext)
```
Get-ChildItem -Path "C:\Users\beaud\AppData\Local\Programs\Termius\Termius.exe" -Recurse | ForEach-Object {
    Set-ItemProperty -Path $_.FullName -Name 'Zone.Identifier' -Value $null -ErrorAction SilentlyContinue
}
```
4. Start Termius, log in to your account, and restart Termius

*********************************
