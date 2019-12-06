# NOIR_intel
intel网卡驱动patch，支持任意频段。

ath网卡：

https://medium.com/@renaudcerrato/how-to-build-your-own-wireless-router-from-scratch-part-3-d54eecce157f

intel网卡：

patch 两个模块

iwlwifi.ko

iwlmvm.ko

iwl-eeprom-parse.c

注释

​	/*if (!(nvm_flags & NVM_CHANNEL_IBSS))

​		flags |= IEEE80211_CHAN_NO_IR;

​	if (!(nvm_flags & NVM_CHANNEL_ACTIVE))

​		flags |= IEEE80211_CHAN_NO_IR;*/

/*if (!(nvm_flags & NVM_CHANNEL_ACTIVE))

​		flags |= NL80211_RRF_NO_IR;*/

共三处。

iwl-nvm-parse.c

/*if (!(nvm_flags & NVM_CHANNEL_IBSS))

​		flags |= IEEE80211_CHAN_NO_IR;

​	if (!(nvm_flags & NVM_CHANNEL_ACTIVE))

​		flags |= IEEE80211_CHAN_NO_IR;*/

/*if (!(nvm_flags & NVM_CHANNEL_ACTIVE))

​		flags |= NL80211_RRF_NO_IR;*/

共三处

mvm目录下：

mac80211.c

//hw->wiphy->regulatory_flags |= REGULATORY_ENABLE_RELAX_NO_IR;

共一处