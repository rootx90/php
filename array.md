### شرح واستخدام دوال المصفوفات في PHP مع أمثلة من تطبيقات الواقع

في لغة PHP، هناك العديد من الدوال المفيدة للتعامل مع المصفوفات (Arrays)، والتي تجعل معالجة البيانات أكثر كفاءة وسهولة. في هذا الشرح، سأستعرض كل دالة من الدوال المذكورة في الاستعلام، مع توضيح متى نستخدمها، وأمثلة عملية من تطبيقات الواقع، وكيف تساعدنا في تطوير التطبيقات.

---

#### 1. **is_array()**
- **الوصف**: تتحقق مما إذا كان المتغير مصفوفة أم لا، وتعيد `true` إذا كان مصفوفة و `false` إذا لم يكن.
- **متى نستخدمها**: عندما نحتاج للتأكد من نوع البيانات قبل إجراء عمليات عليها لتجنب الأخطاء.
- **مثال من الواقع**: في تطبيق ويب يتلقى بيانات من نموذج، قد نريد التحقق مما إذا كانت البيانات المدخلة مصفوفة (مثل قائمة خيارات متعددة).
- **كيف تساعدنا**: تمنع حدوث أخطاء عند محاولة معالجة متغير ليس مصفوفة كمصفوفة.
- **مثال بالكود**:
  ```php
  $data = ["apple", "banana"];
  if (is_array($data)) {
      echo "هذا متغير مصفوفة!";
  }
  ```

---

#### 2. **array_unique()**
- **الوصف**: تزيل القيم المكررة من المصفوفة وتعيد مصفوفة جديدة.
- **متى نستخدمها**: عندما نريد قائمة فريدة من القيم فقط.
- **مثال من الواقع**: في نظام إدارة مخزون، يمكن استخدامها لمعرفة الأصناف الفريدة المباعة في يوم معين.
- **كيف تساعدنا**: تبسط تحليل البيانات بإزالة التكرارات.
- **مثال بالكود**:
  ```php
  $sales = ["phone", "laptop", "phone", "tablet"];
  $unique_sales = array_unique($sales);
  print_r($unique_sales); // ["phone", "laptop", "tablet"]
  ```

---

#### 3. **array_search()**
- **الوصف**: تبحث عن قيمة في المصفوفة وتعيد مفتاحها إذا وجدت، أو `false` إذا لم توجد.
- **متى نستخدمها**: عند الحاجة لمعرفة موقع قيمة معينة في المصفوفة.
- **مثال من الواقع**: في نظام إدارة مستخدمين، البحث عن اسم مستخدم للحصول على معرفه الفريد (ID).
- **كيف تساعدنا**: توفر طريقة سريعة لتحديد موقع البيانات.
- **مثال بالكود**:
  ```php
  $users = ["ahmed", "mohamed", "ali"];
  $key = array_search("mohamed", $users);
  echo $key; // 1
  ```

---

#### 4. **array_reverse()**
- **الوصف**: تعكس ترتيب العناصر في المصفوفة.
- **متى نستخدمها**: عندما نريد عرض البيانات بترتيب عكسي.
- **مثال من الواقع**: عرض أحدث التعليقات أولاً في مدونة.
- **كيف تساعدنا**: تسهل عرض البيانات بالترتيب المطلوب دون تعديل يدوي.
- **مثال بالكود**:
  ```php
  $comments = ["first", "second", "third"];
  $reversed = array_reverse($comments);
  print_r($reversed); // ["third", "second", "first"]
  ```

---

#### 5. **array_reduce()**
- **الوصف**: تقلل المصفوفة إلى قيمة واحدة باستخدام دالة callback.
- **متى نستخدمها**: عند الحاجة لعملية تراكمية مثل جمع الأرقام.
- **مثال من الواقع**: حساب مجموع أسعار المنتجات في سلة التسوق.
- **كيف تساعدنا**: تجعل العمليات الحسابية أسهل وأكثر تنظيماً.
- **مثال بالكود**:
  ```php
  $prices = [10, 20, 30];
  $total = array_reduce($prices, function($carry, $item) {
      return $carry + $item;
  }, 0);
  echo $total; // 60
  ```

---

#### 6. **array_map()**
- **الوصف**: تطبق دالة على كل عنصر في المصفوفة وتعيد مصفوفة جديدة.
- **متى نستخدمها**: عندما نريد تعديل جميع العناصر دون تغيير المصفوفة الأصلية.
- **مثال من الواقع**: تطبيق زيادة بنسبة 10% على أسعار المنتجات.
- **كيف تساعدنا**: توفر طريقة نظيفة لتحويل البيانات.
- **مثال بالكود**:
  ```php
  $prices = [100, 200, 300];
  $new_prices = array_map(function($price) {
      return $price * 1.10;
  }, $prices);
  print_r($new_prices); // [110, 220, 330]
  ```

---

#### 7. **array_filter()**
- **الوصف**: تصفي المصفوفة بناءً على شرط وتعيد مصفوفة جديدة.
- **متى نستخدمها**: عندما نريد استخراج عناصر معينة بناءً على معيار.
- **مثال من الواقع**: عرض المهام المكتملة فقط في نظام إدارة مهام.
- **كيف تساعدنا**: تقلل الحاجة للحلقات اليدوية للتصفية.
- **مثال بالكود**:
  ```php
  $tasks = ["done", "pending", "done"];
  $completed = array_filter($tasks, function($task) {
      return $task === "done";
  });
  print_r($completed); // ["done", "done"]
  ```

---

#### 8. **max()**
- **الوصف**: تعيد أكبر قيمة في المصفوفة.
- **متى نستخدمها**: عند الحاجة لمعرفة القيمة القصوى.
- **مثال من الواقع**: إيجاد أعلى درجة في اختبار.
- **كيف تساعدنا**: تسرع عملية استخراج القيم القصوى.
- **مثال بالكود**:
  ```php
  $scores = [85, 92, 78];
  echo max($scores); // 92
  ```

---

#### 9. **min()**
- **الوصف**: تعيد أصغر قيمة في المصفوفة.
- **متى نستخدمها**: عند الحاجة لمعرفة القيمة الدنيا.
- **مثال من الواقع**: إيجاد أقل سعر لمنتج في متجر إلكتروني.
- **كيف تساعدنا**: تبسط مقارنة البيانات.
- **مثال بالكود**:
  ```php
  $prices = [150, 120, 180];
  echo min($prices); // 120
  ```

---

#### 10. **array_rand()**
- **الوصف**: تختار مفتاحاً عشوائياً من المصفوفة.
- **متى نستخدمها**: عند الحاجة لاختيار عنصر عشوائي.
- **مثال من الواقع**: اختيار فائز عشوائي في مسابقة.
- **كيف تساعدنا**: توفر طريقة بسيطة للعشوائية.
- **مثال بالكود**:
  ```php
  $participants = ["Ali", "Sara", "Omar"];
  $winner_key = array_rand($participants);
  echo $participants[$winner_key]; // قد يطبع "Sara"
  ```

---

#### 11. **array_count_values()**
- **الوصف**: تعد تكرار كل قيمة في المصفوفة وتعيد مصفوفة بالنتائج.
- **متى نستخدمها**: عند الحاجة لإحصاء التكرارات.
- **مثال من الواقع**: إحصاء الإجابات في استطلاع رأي.
- **كيف تساعدنا**: توفر تحليل بيانات سريع.
- **مثال بالكود**:
  ```php
  $votes = ["yes", "no", "yes"];
  $counts = array_count_values($votes);
  print_r($counts); // ["yes" => 2, "no" => 1]
  ```

---

#### 12. **implode()**
- **الوصف**: تحول المصفوفة إلى سلسلة نصية بفاصل محدد.
- **متى نستخدمها**: عند الحاجة لعرض المصفوفة كنص.
- **مثال من الواقع**: عرض قائمة أسماء مفصولة بفواصل.
- **كيف تساعدنا**: تجعل تنسيق البيانات أسهل.
- **مثال بالكود**:
  ```php
  $names = ["Ali", "Sara", "Omar"];
  echo implode(", ", $names); // "Ali, Sara, Omar"
  ```

---

#### 13. **array_pop()**
- **الوصف**: تزيل العنصر الأخير من المصفوفة وتعيده.
- **متى نستخدمها**: عند الحاجة لإزالة وحفظ العنصر الأخير.
- **مثال من الواقع**: تنفيذ هيكل بيانات المكدس (Stack).
- **كيف تساعدنا**: تسهل إدارة البيانات الديناميكية.
- **مثال بالكود**:
  ```php
  $stack = [1, 2, 3];
  $last = array_pop($stack);
  echo $last; // 3
  print_r($stack); // [1, 2]
  ```

---

#### 14. **array_shift()**
- **الوصف**: تزيل العنصر الأول من المصفوفة وتعيده.
- **متى نستخدمها**: عند الحاجة لإزالة وحفظ العنصر الأول.
- **مثال من الواقع**: تنفيذ هيكل بيانات الطابور (Queue).
- **كيف تساعدنا**: تدعم معالجة البيانات بالترتيب.
- **مثال بالكود**:
  ```php
  $queue = [1, 2, 3];
  $first = array_shift($queue);
  echo $first; // 1
  print_r($queue); // [2, 3]
  ```

---

#### 15. **sort()**
- **الوصف**: ترتب المصفوفة بترتيب تصاعدي.
- **متى نستخدمها**: عند الحاجة لترتيب البيانات تصاعدياً.
- **مثال من الواقع**: ترتيب قائمة أسماء أبجدياً.
- **كيف تساعدنا**: تجعل البيانات أكثر تنظيماً.
- **مثال بالكود**:
  ```php
  $names = ["Omar", "Ali", "Sara"];
  sort($names);
  print_r($names); // ["Ali", "Omar", "Sara"]
  ```

---

#### 16. **rsort()**
- **الوصف**: ترتب المصفوفة بترتيب تنازلي.
- **متى نستخدمها**: عند الحاجة لترتيب البيانات تنازلياً.
- **مثال من الواقع**: ترتيب النتائج من الأعلى إلى الأدنى.
- **كيف تساعدنا**: توفر ترتيباً عكسياً بسهولة.
- **مثال بالكود**:
  ```php
  $scores = [85, 92, 78];
  rsort($scores);
  print_r($scores); // [92, 85, 78]
  ```

---

#### 17. **array_walk()**
- **الوصف**: تطبق دالة على كل عنصر ويمكنها تعديل المصفوفة الأصلية.
- **متى نستخدمها**: عند الحاجة لتغيير العناصر في المصفوفة الأصلية.
- **مثال من الواقع**: زيادة كل سعر في قائمة بنسبة معينة.
- **كيف تساعدنا**: تتيح التعديل المباشر على المصفوفة.
- **مثال بالكود**:
  ```php
  $prices = [100, 200, 300];
  array_walk($prices, function(&$price) {
      $price *= 1.10;
  });
  print_r($prices); // [110, 220, 330]
  ```

---

### الفائدة العامة لهذه الدوال
تساعدنا هذه الدوال في:
- **توفير الوقت والجهد**: بدلاً من كتابة حلقات معقدة، تقدم حلولاً جاهزة.
- **تحسين جودة الكود**: تجعل الشيفرة أكثر وضوحاً ونظافة.
- **معالجة البيانات بكفاءة**: سواء كان ذلك بالترتيب، التصفية، أو التحويل.

بهذا الشكل، تصبح المصفوفات في PHP أداة قوية لتطوير تطبيقات عملية وفعالة!
