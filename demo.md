```java
@Test
    void demoTest(@Autowired Neo4jTemplate neo4jTemplate){
        // 删除所有节点和关系（删除节点会响应删除关联关系），避免后续创建节点重复影响
        neo4jTemplate.deleteAll(Disease.class);
        neo4jTemplate.deleteAll(Symptom.class);
        neo4jTemplate.deleteAll(Cause.class);
        neo4jTemplate.deleteAll(ExaminationMethod.class);
        neo4jTemplate.deleteAll(TreatmentMethod.class);


        Disease depression = new Disease("抑郁症","depression","","抑郁症");
        Disease mildDepression = new Disease("轻度抑郁症","mild depression","","轻度抑郁症长期表现为有情绪低落、不合群、离群、躯体不适、食欲不振及睡眠障碍。");
        Disease postpartumDepression = new Disease("产后抑郁症","postpartum depression","","产后抑郁症（postpartum depression）是指女性于产褥期出现明显的抑郁症状或典型的抑郁发作，与产后心绪不宁和产后精神病同属产褥期精神综合征。发病率在15%～30%。典型的产后抑郁症于产后6周内发生，可在3～6个月自行恢复，但严重的也可持续1～2年，再次妊娠则有20%～30%的复发率。其临床特征与其他时间抑郁发作无明显区别。");

        Symptom symptom1 = new Symptom("情绪低落","情绪低落","轻微");
        Symptom symptom2 = new Symptom("不合群","不合群","轻微");
        Symptom symptom3 = new Symptom("食欲不振","食欲不振","轻微");
        Symptom symptom4 = new Symptom("睡眠障碍","睡眠障碍","轻微");
        Symptom symptom5 = new Symptom("易困倦","易困倦","轻微");
        Symptom symptom6 = new Symptom("易流泪","易流泪","轻微");

        Cause cause1 = new Cause("内分泌因素"," 在妊娠分娩的过程中，体内内分泌环境发生了很大变化，尤其是产后24小时内，体内激素水平的急剧变化是产后抑郁症发生的生物学基础。");
        Cause cause2 = new Cause("遗传因素","有精神病家族史，特别是有家族抑郁症病史的产妇，产后抑郁的发病率高。");
        Cause cause3 = new Cause("社会心理因素","产妇人格特征、分娩前心理准备不足、产后适应不良、产后早期心绪不良、睡眠不足、照顾婴儿过于疲劳、产妇年龄小、夫妻关系不和、缺乏社会支持、家庭经济状况、分娩时医务人员态度、婴儿性别和健康状况等等，均与产后抑郁症的发生密切相关。");

        ExaminationMethod examinationMethod1 = new ExaminationMethod("量表测试");
        ExaminationMethod examinationMethod3 = new ExaminationMethod("医生问诊");
        ExaminationMethod examinationMethod2 = new ExaminationMethod("生物样本检测");

        TreatmentMethod treatmentMethod1 = new TreatmentMethod("自我鼓励法","");
        TreatmentMethod treatmentMethod2 = new TreatmentMethod("自我实现法","");
        TreatmentMethod treatmentMethod3 = new TreatmentMethod("支持性心理治疗","");
        TreatmentMethod treatmentMethod4 = new TreatmentMethod("人际心理治疗","");
        TreatmentMethod treatmentMethod5 = new TreatmentMethod("音乐疗法","");
        TreatmentMethod treatmentMethod6 = new TreatmentMethod("焦点转移","");
        TreatmentMethod treatmentMethod7 = new TreatmentMethod("倾诉宣泄法","");
        TreatmentMethod treatmentMethod8 = new TreatmentMethod("角色交替法","");

        depression.getDiseaseTypes().add(mildDepression);
        depression.getDiseaseTypes().add(postpartumDepression);

        mildDepression.getSymptomList().add(symptom1);
        mildDepression.getSymptomList().add(symptom2);
        mildDepression.getSymptomList().add(symptom3);
        mildDepression.getSymptomList().add(symptom4);

        postpartumDepression.getSymptomList().add(symptom1);
        postpartumDepression.getSymptomList().add(symptom5);
        postpartumDepression.getSymptomList().add(symptom6);

        postpartumDepression.getCauseList().add(cause1);
        postpartumDepression.getCauseList().add(cause2);
        postpartumDepression.getCauseList().add(cause3);

        mildDepression.getExaminationMethodList().add(examinationMethod1);
        mildDepression.getExaminationMethodList().add(examinationMethod2);
        mildDepression.getExaminationMethodList().add(examinationMethod3);

        postpartumDepression.getExaminationMethodList().add(examinationMethod1);
        postpartumDepression.getExaminationMethodList().add(examinationMethod2);
        postpartumDepression.getExaminationMethodList().add(examinationMethod3);


        mildDepression.getTreatmentMethodList().add(treatmentMethod1);
        mildDepression.getTreatmentMethodList().add(treatmentMethod2);
        mildDepression.getTreatmentMethodList().add(treatmentMethod3);
        mildDepression.getTreatmentMethodList().add(treatmentMethod4);
        mildDepression.getTreatmentMethodList().add(treatmentMethod5);
        mildDepression.getTreatmentMethodList().add(treatmentMethod6);
        mildDepression.getTreatmentMethodList().add(treatmentMethod7);


        postpartumDepression.getTreatmentMethodList().add(treatmentMethod1);
        postpartumDepression.getTreatmentMethodList().add(treatmentMethod2);
        postpartumDepression.getTreatmentMethodList().add(treatmentMethod3);
        postpartumDepression.getTreatmentMethodList().add(treatmentMethod4);
        postpartumDepression.getTreatmentMethodList().add(treatmentMethod5);
        postpartumDepression.getTreatmentMethodList().add(treatmentMethod6);
        postpartumDepression.getTreatmentMethodList().add(treatmentMethod7);
        postpartumDepression.getTreatmentMethodList().add(treatmentMethod8);

        neo4jTemplate.save(depression);
        neo4jTemplate.save(mildDepression);
        neo4jTemplate.save(postpartumDepression);

        neo4jTemplate.save(symptom1);
        neo4jTemplate.save(symptom2);
        neo4jTemplate.save(symptom3);
        neo4jTemplate.save(symptom4);
        neo4jTemplate.save(symptom5);
        neo4jTemplate.save(symptom6);

        neo4jTemplate.save(cause1);
        neo4jTemplate.save(cause2);
        neo4jTemplate.save(cause3);

        neo4jTemplate.save(examinationMethod1);
        neo4jTemplate.save(examinationMethod2);
        neo4jTemplate.save(examinationMethod3);

        neo4jTemplate.save(treatmentMethod1);
        neo4jTemplate.save(treatmentMethod2);
        neo4jTemplate.save(treatmentMethod3);
        neo4jTemplate.save(treatmentMethod4);
        neo4jTemplate.save(treatmentMethod5);
        neo4jTemplate.save(treatmentMethod6);
        neo4jTemplate.save(treatmentMethod7);
        neo4jTemplate.save(treatmentMethod8);
    }
```

