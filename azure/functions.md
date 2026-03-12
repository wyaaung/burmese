# Functions

Azure Functions ဆိုတာ Serverless Computing (ကိုယ်ပိုင် Server မလို၊ Code ပဲရေးပြီး Event ဖြစ်ရင် Azure က Auto Run ပေးတဲ့ Computing ပုံစံ) ပါ။ Code ရေးပြီး Event လာရင် Auto Run ပါတယ်။ Server Manage မလုပ်ရပါဘူး။

Function တစ်ခုမှာ Event Trigger (ဘာဖြစ်ရင် Function ကို Run ရမလဲ) နဲ့ Binding(Data ကို ဘယ်ကနေ ယူမလဲ / ဘယ်ကို ပို့မလဲ) ဆိုပြီး Configure လုပ်ရပါတယ်။

Programming Language အလိုက် Configure လုပ်ပုံ မတူပါဘူး။

Python v1 Programming Model မှာ function.json ဆိုတဲ့ File ထဲမှာ JSON Format နဲ့ Define လုပ်ရပါတယ်။ Code နဲ့ Configuration ကို File ခွဲထားတာပါ။

Python v2 Programming Model မှာတော့ Python Decorators (@app.route() လိုမျိုး) သုံးပြီး Code ထဲမှာ တိုက်ရိုက် Define လုပ်ပါတယ်။

Java မှာတော့ Annotations(@FunctionName, @HttpTrigger) သုံးပြီး Code ထဲမှာ Define လုပ်ပါတယ်။

C# မှာတော့ Attributes([HttpTrigger]) သုံးပါတယ်။ Java ရဲ့ Annotation နဲ့ C# ရဲ့ Attribute ဆိုတာ Language ကွာပေမယ့် Concept အတူတူပါပဲ။

host.json ဆိုတာကတော့ Function App တစ်ခုလုံးအတွက် Global Runtime Settings ကို Configure လုပ်တဲ့ File ပါ (Logging, Timeout စသဖြင့်)။ Trigger/Binding Define လုပ်တဲ့ File မဟုတ်ပါဘူး။
