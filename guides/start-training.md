---
description: Ways how to start training in FELT.
---

# Start training

FELT provides 3 ways how to start the training:
- Browser flow with wallet signing
- Browser flow with Auto-Sign
- Python flow

Let's go through each of them.

## Browser flow with wallet signing

Any transaction on a blockchain has to be approved through your wallet. This ensures higher security, but it can slow things down when needing to approve multiple transactions. 

## Browser flow with Auto-Sign

Instead of manually signing transactions, you can use the Auto-Sign feature. This feature will automatically sign all transactions using separated account. This makes the training process smoother.

### How to setup Auto-Sign

To setup Auto-Sign, go to your FELT [account page](https://app.feltlabs.ai/account):

1. Connect your MetaMask account using **Connect Wallet** button.
2. Click on **Setup Auto-Sign** button
3. You will be given a randomly generated private key. If you want, you can also paste your own private key.
4. Fill in the password which is used to encrypt the private key and click **Submit**

Now you see that a new account was generated for you. The current balance is zero. You have to use the **top-up** button to add Matic and Ocean to this account.

1. Select the amount of Matic/Ocean and click **Top Up**
2. **Confirm** the transaction using MetaMask

This will transfer the funds from your MetaMask account to the account used for automation. You can also use **Withdraw All** button to get all funds back to your MetaMask account.

Now you can start training using Auto-Sign. For that you just need to activate it by providing the password you used to encrypt the private key.

{% hint style="danger" %}
Do not lose your password. If you lose it, you will not be able to restore the account. We also recommend to backup the private key.
{% endhint %}

### Storing the Account

The account is stored encrypted by the password in our database. Next time you would like to use this account you will just activate it by providing a password. Be aware that if you lose the password, you are not able to restore the account.

## Python flow

Python flow is the most seamless and secure way how to start training. It allows you to use any wallet account. This account is not shared with anyone. It is used to automatically sign transactions through python. 

Instruction how to set it up can be found here:

{% embed url="https://github.com/FELT-Labs/python-flow" %}
