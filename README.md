# React hooks with TypeScript


## سوف نتعلم في هذا الدرس :
- التعامل مع useState
- التعامل مع useEffect




سابقٍا كان React  يتعامل مع المكونات كـclass components حيث اننا اولا نقوم بالوراثه من Component ونقوم بإستخدام دالة render ، وتزداد الأمور تعقيدٍا مع كتابة الكثير من الأوامر .


## مثال :


    import React, { Component } from 'react'
    export default class componentName extends Component {
      render() {
        return (
          <>
            
          </>
        )
      }
    }

لكن بعد ان تم تقديم hooks في النسخه 16.8. من React تغيرت الأمور ، حيث اصبح بإمكاننا التعامل مع جميع محتويات class components لكن بكتابة اوامر اقل وابسط ،على عكس class تتعامل hooks مع Function 

سنقوم بالتعرف على اشهر hooks المستخدمه من قبل React .


## الحالات useState :

كما ذكرنا سابقا  اننا نستطيع الكتابه بداخل components بتمرير props اليها لكننا لا نستطيع التعديل على النص كمستخدمين وهذا ماقد يسبب مشاكل كثيرة حيث ان قيمتها ثابتة ونحتاج لتعديلها العوده الى الكود وتغيير قيمتها ، لكن ماذا لو اردنا ان يقوم المستخدم بالضغط على الزر وتغيير العدد مثلٍا ، او إدخال بياناته الشخصيه ؟ في هذه الحالة سوف نقوم باللجوء الى استخدام hooks وواحده من اشهر hooks هي useState حيث تسمح للمستخدم بتغيير القيمة الأوليه للحالة 
ولكي نستطيع استخدامها نحتاج اولٍا  لإنشاء Function Component واسناد له إسم ، في حالتنا هذه سوف نقوم بتسميته Hooks ونقوم بكتابة الإختصار rfc ليقوم المحرر بمساعدتنا في انشاء المحتوى الرئيسي 


## مثال :
    // لقد قمنا بكتابة الأمر rfc لينشئ لنا المحتوى الموجود بالأسفل
    
    import React from "react";
    export default function Hooks() {
      return <div>Hooks</div>;
    }
    

دعونا اولٍا نتصور مالذي نحتاجه وماهي النتيجة النهائية له .

لنفترض ان لدينا زر وفي كل مرة يتم الضغط عليه تزداد قيمة العداد ، هذا يعني اننا سنقوم بإنشاء counter يحسب لنا عدد الضغطات . 

وبعد انشاء المكون سوف نقوم بإستدعاء useState ، لا نحتاج لإستخدام npm لتحميلها ، كل ماعلينا فعله هو كتابتها في الأعلى وبهذا سوف يقوم بإستدعائها 


## مثال :


    import React ، {useState} from "react";
    export default function Hooks() {
      return <div>Hooks</div>;
    }

نلاحظ اننا استخدمنا distractor وهذا يعني ان React يدعمها وانها احد محتوياته .

مع استخدام typescript سوف نلاحظ ظهور تنبيه يُفيد اننا قمنا بإضافة useState لكننا لم نستخدمها 

ولإستخدامها  علينا اولٍا معرفة الطريقة الصحيحه لكتابتها ومكان كتابتها .

يتم كتابة useState في الأعلى دائمٍا اسفل اسم Function Component في حال قمنا بكتابتها في مكان اخر سوف تظهر لنا بعض الأخطاء لذا فضل دائما كتابتها في الأعلى 


## مثال :


    import React, { useState } from "react";
    export default function Hooks() {
      const [state, setstate] = useState(initialState);
      return <div>Hooks</div>;
    }
    

نلاحظ مكان وطريقة الكتابة ،
حيث اولٍا قمنا بكتابة الثابت const ومن ثم استخدمنا اقواس المصفوفه ، بداخلها نقوم بكتابة اسم الحالة التي نريدها حيث تمثل state الحالة الأوليه ، بمثل لو كان لدينا عداد يقوم بحسابة عدد الضغطات سوف يقوم بالعد من الرقم صفر لذا قيمة state ستكون صفر ، ولكي نستطيع تغيير قيمة الصفر الى قيمة أخرى يجب علينا اولٍا استخدام setstate وهي عبارة عن function نقوم بتمرير الأمر البرمجي لها وبذالك يستطيع التأثير على القيمة الأولية state . 
ونقوم بعدها بكتابة  useState(initialState) وكما نلاحظ اننا نقوم بتمرير initialState بداخل useState function وهذا يعني القيمة الأوليه state لذا سوف نقوم بتمرير الرقم صفر بداخلها .

حسنٍا لنعود للمثال وكتابته  


    import React, { useState } from "react";
    export default function Hooks() {
      const [counter, setCounter] = useState(0);
      return <div>Hooks</div>;
    }

*ملاحظة :  يتم كتابة اول حرف بعد set بشكل كبير للتفرقه بينه وبين الحاله الأصليه state 

لنقوم الأن بكتابة الزر الخاص بنا 


    import React, { useState } from "react";
    export default function Hooks() {
      const [counter, setCounter] = useState(0);
      return (
        <div>
          <button>Click me </button>
        </div>
      );
    }
    

سنقوم الان بالذاهب الى App.tsx واستدعاء مكوننا فيه حتى نستطيع رؤيته على الشاشه 

    import Hooks from "./component/Hooks";
    

ومن ثم سوف نقوم بإستدعاد المكون بالأسفل 

    <Hooks/>

 
 حين نقوم بتشغيل المشروع والذهاب للمتصفح سوف نلاحظ وجود زر Click me لكن عند الضغط عليه لا يحدث اي تفاعل ! وهذا بسبب اننا لم نقم بتمرير اي اكشن للزر 
 
 الخطوة التاليه هي تمرير function الخاصه بالعداد الى الزر الخاص بنا 
 

     import React, { useState } from "react";
    export default function Hooks() {
      const [counter, setCounter] = useState(0);
      return (
        <div>
          <button onClick={() => setCounter()}>Click me </button>
        </div>
      );
    }

نلاحظ اننا قمنا بكتابة الحدث onClick  وذالك ليقوم بالتعرف على اي اكشن سوف يقوم به المستخدم ، بمعنى اننا اخبرنا في كل مره يقوم المستخدم بالضغط على هذا الزر onClick قم بالتفاعل معه على حسب ماهو مطلوب .

ومن ثم قمنا بتمرير setCounter بداخلها كما ذكرنا سابقٍا انها function وللوصول للحالة الأولية state والتي تحمل القيمة صفر والتعديل عليها يجب علينا اولٍا المرور من function الخاصه بها وفي حالتنا هذه تُعتبر setCounter لذا سوف نقوم بتمرير الحالة الأوليه فيها ومن ثم اضافة التعديل عليها .

مثال :

    import React, { useState } from "react";
    export default function Hooks() {
      const [counter, setCounter] = useState(0);
      return (
        <div>
          <button onClick={() => setCounter(counter + 1)}>Click me </button>
        </div>
      );
    }
    

لقد قمنا بتمرير القيمة الأولية counter وااضافة التعديل المراد عليه وفي حالتنا هذه نريد منه اضافة عدد واحد في كل مره يتم الضغط عليه.

عند الذهاب الى المتصفح والضغط على الزر الخاص بنا نلاحظ انه لم يحدث اي تغير ولا يوجد اي خطأ ! 

ويعود السبب الى اننا لم نقم بتوفير مكان للعداد واستدعاء الحالة الأوليه لكي تتفاعل مع التحديثات 


    import React, { useState } from "react";
    export default function Hooks() {
      const [counter, setCounter] = useState(0);
      return (
        <div>
          <button onClick={() => setCounter(counter + 1)}>Click me </button>
          <p>You clicked {counter} times</p>
        </div>
      );
    }
    

الأن حين نقوم بالذهاب للمتصفح ومحاولة الضغط على الزر نلاحظ انه يقوم بالتعديل على القيمة الأولية بإضافة رقم واحد عليها ونستطيع التغير علي العدد فلو اردنا يقوم بالعد كل خطوتين نستطيع التعديل على القيمة 

مثال :


          <button onClick={() => setCounter(counter + 2)}>Click me </button>

نقوم بالإستنتاج انه حين استخدام useState فإن المستخدم يستطيع تحديث الحاله والتغيير من قيمتها الأولية بالتعديل عليها بعكس props .

لكن نلاحظ حتى هذه اللحظه لم نستخدم useState مع typescript ، لكن هل يحدث تغيير كبير ؟ 

كما ذكرنا سابقًا انه مع استخدام typescript يجب علينا تحديد نوع المدخل ، في الحقيقة عند كتابة القيمة الأوليه وهي العدد صفر بداخل useState تم التعرف على انها سوف تستقبل متغير من النوع number .


لكن في حال لدينا اكثر من نوع فيمكننا تمريره بهذه الطريقة 


    const [counter, setCounter] = useState<number>(0);

نلاحظ اننا قمنا بكتابة النوع بجانب useState لنقوم بإخباره ان المدخلات اللتي سوف يستقبلها من النوع number

ــــــــــــــــــــــ


## التعامل مع UseEffect :

تعتبر `useEffect` ثاني أشهر Hook، تضيف القدرة على إضافة تأثيرات جانبية مثل `componentDidMount` و  `componentDidUpdate` و `componentWillUnmount` المستعملة في الـClasses، لكنها هنا مدموجة في API واحد.
حيث انها تحتوي على الحاله الأوليه للمكون وحالته حين التحديث عليه وبعد الإنتهاء منه والإنتقال الى مكون أخر 


    import { useState, useEffect } from 'react';
    
    function App() {
      const [increament, setIncreament] = useState(3);
    
      useEffect(() => {
        changeValue();
        return () => {
        }
      }, [])
      const changeValue = () => {
        setIncreament(5);
      }
      return (
        <div className="App">
          {increament}
        </div>
      );
    }
    export default App;

سوف نستبين اهميتها في التعامل مع API خارجي لكن كما نلاحظ هنا انه تم تمرير دالة changeValue من خلال useEffect والتي ستحسب لنا الحالة الأوليه لها والتي ستكون 3 ومن ثم سيقوم بتحديث الصفحه عند التعديل على القيمة  وتحديثها مرة أخرى حين الإنتهاء 

