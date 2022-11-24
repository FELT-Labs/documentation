---
description: Guide to using Activate Automation option in web application.
---

# Automation

Any transaction on a blockchain has to be approved through your wallet. This ensures higher security, but it can slow things down when needing to approve multiple transactions. In the FELT application, you can choose between approving every transaction or using automation. Automating transactions makes the training process smoother. This tutorial will first explain how to set up the automation and then explain how it works underneath.

## Activating Automation

To activate the automation, you have to go to [app.feltlabs.ai](https://app.feltlabs.ai/) and do the following steps:

1. Connect your MetaMask account using **Connect** button. You can read more about [installing MetaMask here](https://metamask.io/download).
2. Click on **Add Automation** in the top-right corner next to the MetaMask connect button.
3. MetaMask will show a pop-up asking you to provide a Publick key; click on **Provide**

Right now, you have your automation account created. The next step is to top-up the account with some Matick and Ocean tokens. Click on the **Automation** button next to MetaMask connect to open automation account details.

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption><p>Automation account balance and posibility to add balance to it.</p></figcaption></figure>

In account details, you see that a new account was generated for you. The current balance is zero. You have to use the **top-up** button to add Matic and Ocean to this account.

1. Select the amount of Matic/Ocean and click **Top Up**
2. **Confirm** the transaction using MetaMask

This will transfer the funds from your MetaMask account to the account used for automation. You can also use **Withdraw All** button to get all funds back to your MetaMask account.

After that, you can just close the windows and start using the FELT application. The automation account will be used automatically for all the transactions.

### Storing the Account

The account will be encrypted and automatically stored in the storage of your browser. Anytime you return back to [app.feltlabs.ai](https://app.feltlabs.ai/), you can click on **Activate Automation** which will restore the account from the previous session. You just need to approve the decryption of the account in your MetaMask account. This ensures that you don't loos any funds in the automation account even after closing the browser.

## How It Works?

The automation generates a separate blockchain address and private key, we will call this automation account. The application can then use the private key to automatically sign the necessary transactions. The automation account (private key) never leaves your computer, and all transactions are signed locally. However, for security reasons, we still recommend topping up only funds necessary for training.

The automation account is encrypted using an account stored in MetaMask and then stored in the local storage of your browsers. So anytime you want to restore the automation account, you have to decrypt it using MetaMask. This ensures a higher level of security as the potential leak of local storage only leaks the encrypted account. However, anyone with access to your MetaMask account can also decrypt your automation account.
