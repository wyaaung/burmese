# VPC

AWS VPC က Virtual Private Cloud ဖြစ်ပြီးတော့ Regional Service ဖြစ်လို့ region တစ်ခုထဲမှာပဲ အလုပ်လုပ်ပါတယ်။ us-east-1 မှာ VPC တစ်ခု, ap-southeast-1 မှာ နောက်တစ်ခု, eu-west-1 မှာ နောက်တစ်ခု ဆိုပြီး region တိုင်းမှာ separate VPCs တွေ တည်ဆောက်ရပါတယ်။ ဒီ VPCs တွေကြား connectivity လိုချင်ရင် VPC Peering ဒါမှမဟုတ် Transit Gateway သုံးပြီး explicitly connect လုပ်ရပါမယ်။

AWS မှာ multi-region deployments တွေအတွက် networking complexity ပိုများပါတယ်။ ဒါပေမယ့် AWS က Region-level Isolation ပိုကောင်းတာမို့လို့ ပြဿနာတစ်ခုခုဖြစ်ရင် blast radius ကို control လုပ်လို့ ပိုလွယ်ပါတယ်။

## Region, Availability Zone, Subnets

AWS ရဲ့ Geographic Hierarchy ပါ။

Region က Geographic Area တစ်ခုဖြစ်ပြီး us-east-1 (N. Virginia), ap-southeast-1 (Singapore), eu-west-2 (London) စသည်ဖြင့် ရှိပါတယ်။ AWS Region တစ်ခုစီမှာ Availability Zone (AZ) တစ်ခုနဲ့ တစ်ခုထက်ပိုပြီး​​ ရှိနိုင်တယ်။ us-east-1 မှာ us-east-1a, us-east-1b, us-east-1c, us-east-1d, us-east-1e, us-east-1f ဆိုပြီး AZ ၆ ခု ရှိတယ်။

AZ တစ်ခုစီက Physical Data Center တစ်ခု ဒါမှမဟုတ် Data Centers Cluster တစ်ခု ဖြစ်နိုင်ပြီးတော့ Power, Cooling, Networking ကတော့ သူ့ AZ တစ်ခုစီက သီးသန့်ရှိပါတယ်။ AZ တစ်ခု Failure ဖြစ်လည်း တခြား AZ တွေအပေါ်ကို ဘာမှမသက်ရောက်ပါဘူး။ High Availability အတွက် စဥ်းစားပြီး Architecture ချတဲ့အခါ Workloads တွေကို Multiple AZs တွေမှာ ဖြန့်ထားဖို့ စဥ်းစားသင့်တယ်။

Subnet တစ်ခုစီက AZ-specific ဖြစ်ပါတယ်။ Subnet တစ်ခုက AZ တစ်ခုထဲမှာပဲ ရှိပါတယ်။ Multi-AZ Deployment လုပ်ချင်ရင် AZ တစ်ခုစီအတွက် Subnet တစ်ခုစီ လိုက်ပြီးတော့ Setup လုပ်ရပါမယ်။

## Public vs Private Subnets

Subnets တွေကို Public နဲ့ Private ခွဲခြားနိုင်တယ်။

Public Subnet က Internet ကို တိုက်ရိုက်ဆက်သွယ်လို့ရတဲ့ Subnet အမျိုးအစား ဖြစ်ပြီးတော့ Internet Gateway ကို Route Table ကနေ ဆက်သွယ်ဖို့လုပ်ထားပါတယ်။ Public Subnet မှာ ရှိတဲ့ EC2 Instance တစ်ခုကို Public IP assign လုပ်ထားရင် Internet ကနေ FTP/SSH စသဖြင့်နဲ့ ဆက်သွယ်လို့ရတယ်။ Web Servers, Load Balancers, Bastions တွေကို Public Subnets မှာ ထားကြပါတယ်။

Private Subnet ကတော့ Internet ကနေ တိုက်ရိုက်ဆက်သွယ်လို့မရတဲ့ Subnet  အမျိုးအစား ဖြစ်ပြီးတော့ Internet Gateway ကို Route မထားပါ။ Database Servers, Application Servers, Internal Services တွေကို Private Subnet တွေမှာ ထားပါတယ်။ Security အရ သုံးသင့်တယ်။
