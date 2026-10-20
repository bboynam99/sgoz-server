# Shadowgun: Deadzone Server
**By vurkz-dev**

---

## Deployment on Railway

1. Upload this folder to a GitHub repository
2. In Railway, select **New Project → Deploy from GitHub**
3. Choose your repository — Railway will detect the `Procfile` automatically
4. Once deployed, copy your Railway project URL (e.g. `your-project.railway.app`)

---

## Implemented Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/sgdz/getProductData` | Retrieves game configuration and shop items |
| GET | `/sgdz/userExists` | Checks whether a user account exists |
| POST | `/sgdz/CreateUser` | Registers a new user account |
| GET | `/sgdz/userGetPrimaryKey` | Returns the authentication key for a user |
| GET | `/sgdz/getUsrPerProductData` | Retrieves player data (inventory, stats, etc.) |
| GET | `/sgdz/getUsrData` | Retrieves additional user data (friends list, etc.) |
| POST | `/sgdz/UserAddProductData` | Adds product data to a user's profile |
| POST | `/sgdz/BuyItem` | Processes an item purchase |
| POST | `/sgdz/EquipItem` | Equips an item to the player |
| POST | `/sgdz/UnEquipItem` | Unequips an item from the player |
| POST | `/sgdz/BuyPremiumAccount` | Activates a premium account for the user |
| POST | `/sgdz/BatchCommand` | Executes multiple commands in a single request |
| GET | `/sgdz/getCloudDateTime` | Returns the current server timestamp |
| GET | `/sgdz/getSMJackpot` | Returns the current slot machine jackpot value |
| POST | `/sgdz/SlotMachineSpin` | Processes a slot machine spin |
| GET | `/sgdz/fetchInboxMsgs` | Retrieves inbox messages for the user |
| GET | `/sgdz/clanapi` | Handles clan-related queries |
| GET | `/sgdz/cloudapi` | Handles leaderboard and revision log queries |
| POST | `/sgdz/RequestResetPassword` | Handles password reset requests |

---

## Redirecting the Game Client

To connect the original Shadowgun: DeadZone APK to this revival server,
you must redirect the game's network traffic away from the original dead server.

### Option A — Packet Capture Pro (No PC required)
1. Open **Packet Capture Pro** on your Android device
2. Navigate to the **Rewrite** section
3. Add a new rewrite rule as follows:
   - **Original host:** `madfingerdatastore.appspot.com`
   - **Replace with:** `your-project.railway.app`
4. Enable the rule and start a new capture session
5. Launch the game — it will now connect to your revival server

### Option B — APK Modification (Requires PC)
1. Decompile the APK using `apktool`:
   ```
   apktool d shadowgun.apk -o shadowgun_decompiled
   ```
2. Search for the string `madfingerdatastore.appspot.com` within the decompiled files
3. Replace every occurrence with your Railway URL
4. Recompile the APK:
   ```
   apktool b shadowgun_decompiled -o shadowgun_modified.apk
   ```
5. Sign the APK using `uber-apk-signer`:
   ```
   java -jar uber-apk-signer.jar --apks shadowgun_modified.apk
   ```
6. Install the signed APK on your device

---

## Notes

- All accounts are granted **99,999 Credits** and **9,999 Gold** upon creation
- **Premium status** is enabled by default for all users
- Player data is stored in memory — it will reset upon server restart
- For persistent storage, a database such as **SQLite or PostgreSQL** is recommended for future versions

---

*Shadowgun: DeadZone is the intellectual property of MADFINGER Games.*
*This project is a non-commercial fan revival intended solely for preservation purposes.*
