### if test string equals
用==或!=不能比较string相等，比较的是引用，不会相等（参考java String==）,test ==为false，test!=为true。  
所以!=用`<if test='!"0".equals(platNo)'>`替代，==用`<if test='"0".equals(platNo)'>`替代

