# App Service

Azure App Service ဆိုတာက Web Application တွေကို Azure ပေါ်မှာ Host လုပ်ဖို့ အသုံးပြုတဲ့ Platform-as-a-Service (PaaS) ပါ။

## Publish Setting

Web Application တစ်ခုကို Deployment လုပ်တဲ့အခါ Publish setting ၂ မျိုးရွေးလို့ရပါတယ်။

"Code" ကို ရွေးရင် Azure က Runtime Stack (Application ကို Run ဖို့ လိုအပ်တဲ့ Programming Language Version) ကို ကိုယ့်အတွက် Manage လုပ်ပေးပါတယ်။ ဥပမာ .NET, Java, PHP ထဲကနေ ရွေးလို့ရပါတယ်။ ကိုယ်က Code တင်လိုက်ရုံပဲ။

"Docker Container" ကို ရွေးရင်တော့ ကိုယ့် Docker Image (Application Code နဲ့ Runtime ပါပြီးသား Package) ထဲမှာ Runtime Stack ပါပြီးသားဖြစ်ရပါတယ်။ Azure က Runtime Stack ရွေးခိုင်းတဲ့ Option ကို ပြမှာမဟုတ်ပါဘူး။

## App Service Plan

App Service Plan ဆိုတာ ကိုယ့် Web Application တွေ Run ဖို့ လိုအပ်တဲ့ Compute Resources (CPU, Memory) ကို Define လုပ်တဲ့ Plan တစ်ခုပါ။ Plan တစ်ခုမှာ Windows ဒါမှမဟုတ် Linux ပဲ ရွေးလို့ရပါတယ်။ OS နှစ်မျိုးလုံး Plan တစ်ခုထဲမှာ တစ်ပြိုင်နက်ထည့်လို့ မရပါဘူး။

ဒီတော့ Web App ၄ ခု ရှိတယ်ဆိုပါစို့ - .NET 9, ASP.NET V4.8, Java 21, PHP 8.4 ဆိုရင် App Service Plan ဘယ်နှစ်ခု လိုမလဲ?

ASP.NET V4.8 က .NET Framework (Microsoft ရဲ့ Development Platform အဟောင်း) ပါ။ ဒါက Windows မှာပဲ Run ပါတယ်။ ကျန်တဲ့ .NET 9, Java 21, PHP 8.4 တွေကတော့ Linux မှာ Run လို့ရပါတယ်။ ဒါကြောင့် Plan 1 (Windows) မှာ ASP.NET V4.8 ကို ထည့်ပြီး Plan 2 (Linux) မှာ .NET 9, Java 21, PHP 8.4 သုံးခုလုံးကို ထည့်ပါ။ Runtime Stack(Language Version) မတူပေမယ့် Linux Plan တစ်ခုထဲမှာ အတူတူ ထည့်လို့ရပါတယ်။

အဖြေကတော့ App Service Plan ၂ ခုပဲ လိုပါတယ်။ အဓိက မှတ်ရမှာက Runtime Stack က App Level(Application တစ်ခုချင်းစီ) မှာ Configure လုပ်တာ၊ OS (Windows/Linux) ကတော့ Plan Level(Plan တစ်ခုလုံး) မှာ Configure လုပ်တာပါ။

## Deployment Slots

Deployment Slot ဆိုတာ ကိုယ့် Web Application ရဲ့ Replica တစ်ခုကို URL သပ်သပ်နဲ့ Run ခိုင်းလို့ရတဲ့ Feature ပါ။ Production ကို Deploy မလုပ်ခင် Staging Slot မှာ Test လုပ်လို့ရပါတယ်။ ပြီးရင် Swap လုပ်ပြီး Production ကို ချောမွေ့စွာ ပြောင်းလို့ရပါတယ်။ User တွေ Downtime မခံရပါဘူး။

Pricing Tier အလိုက် Slot ကန့်သတ်ချက်ကတော့ Free, Shared, Basic Tier တွေမှာ Deployment Slots မရပါဘူး။ Standard Tier မှာ အများဆုံး 5 Slots ရပါတယ်။ Premium နဲ့ Isolated Tier တွေမှာတော့ အများဆုံး 20 Slots ရပါတယ်။

## Backup Feature

App Service Backup Feature ကို သုံးချင်ရင် Pricing Tier က Standard သို့မဟုတ် ၎င်းအထက် ဖြစ်ရပါမယ်။ Free, Shared, Basic Tier တွေမှာ Backup Option ကို ရှာလို့ မတွေ့ရပါဘူး။

Backup Options မပေါ်ဘူးဆိုရင် ပထမဆုံးလုပ်ရမှာက App Service Plan ကို Standard Tier ဒါမှမဟုတ် အဲ့ထက်ကို Scale Up လုပ်ရပါမယ်။ Scale Up လုပ်ပြီးမှ Backup Configuration လုပ်လို့ရမှာပါ။

Backup Data သိမ်းဖို့ Azure Storage Account နဲ့ Blob Container လည်း လိုပါသေးတယ်။ ဒါပေမယ့် Pricing Tier Upgrade ကိုအရင် လုပ်ရပါမယ်။
