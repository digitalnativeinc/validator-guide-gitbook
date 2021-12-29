# Polkadot JS Wallet Setup

Now You can set up Your first two accounts. (If You already have 2 accounts in the Polkadot ecosystem which You want to use in Opportunity Testnet please move to section 3.)

If You don’t have any You must create an Opportunity Testnet. (Please note it is recommended to create two accounts: one to use as the stash account and one to use as your controller account).

Click the round button with plus in it indicated by the arrow.

![](<../.gitbook/assets/image (2).png>)

Now there is a very important stage of setting up an account. The arrow indicates Your wallet’s mnemonic seed which is a key to Your account. As You can see in the comment below You should _write down your wallet’s mnemonic seed and keep it in a safe place. The mnemonic can be used to restore your wallet. Keep it carefully to not lose your assets._

This means that if anyone gets access to Your mnemonic seed, will get access to funds stored in this account. So I recommend storing it offline, so in case of a hacker attack on Your computer or a computer failure You don’t lose this key and access to Your funds.

![](<../.gitbook/assets/image (37).png>)

By checking the box indicated by the arrow You confirm that You stored Your wallet’s mnemonic seed safely. When You are ready please click the button leading to _Next step_.

![](<../.gitbook/assets/image (41).png>)

In the screen below You can set up Your account’s parameters, like on which networks in the Polkadot ecosystem Your account can be used, account’s name and safe password.

You can set up that Your account can be used on any chain. This way You will not need to worry about this option when You switch between various networks. That’s why I recommend using this option. In addition, new networks in the Polkadot ecosystem are not usually visible in this box of polkadot.js extension. At this stage You can choose the main live networks like Polkadot, Kusama, HydraDX or Plasm (currently Astar) or simply leave it as it is. Finally You can click the button indicated by the arrow and _Add the account with the generated seed_.

Regarding name, You can use any word but it is better to add a word _stash_ or any other thanks to which You will know that this is a stash account. It will be helpful with recognizing stash and controller accounts.

![](<../.gitbook/assets/image (40).png>)

As You can see Your stash account is set up.

Important thing: You can use Your account in every network in the Polkadot ecosystem but the address of Your account will be different in every of these networks. For example, Your account will have different addresses in the Polkadot network, different in the Kusama network and different in the Opportunity Testnet.

When You have used an option _Allow use on any chain_ Your account __ Your current address is the general address in Substrate framework. Don’t use it to transfer funds to it. The proper address will show up when You connect the extension with a certain network. I will show it later.

![](<../.gitbook/assets/image (16).png>)

We added a stash account. Now it’s time to set up a controller account.

First, click on an orange circle with plus in it on the right upper corner of the extension and then click Create new account.

![](<../.gitbook/assets/image (31).png>)

The further actions are similar to setting up a stash account except account name which should contain word _controller_ or any other thanks to which You will know that this is a controller account.

Now we have two accounts, _stash_ and _controller_.

![](<../.gitbook/assets/image (3).png>)
