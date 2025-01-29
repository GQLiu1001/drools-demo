order.drl
```drools
//订单积分规则
package com.atguigu.drools.order
import com.atguigu.drools.bean.Order

//规则一：100元以下 不加分
rule "order_rule_1"
    when
        $order:Order(amout < 100)
    then
        $order.setScore(0);
        System.out.println("成功匹配到规则一：100元以下 不加分");
end

//规则二：100元 - 500元 加100分
rule "order_rule_2"
    when
        $order:Order(amout >= 100 && amout < 500)
    then
         $order.setScore(100);
         System.out.println("成功匹配到规则二：100元 - 500元 加100分");
end

//规则三：500元 - 1000元 加500分
rule "order_rule_3"
    when
        $order:Order(amout >= 500 && amout < 1000)
    then
         $order.setScore(500);
         System.out.println("成功匹配到规则三：500元 - 1000元 加500分");
end

//规则四：1000元以上 加1000分
rule "order_rule_4"
    when
        $order:Order(amout >= 1000)
    then
         $order.setScore(1000);
         System.out.println("成功匹配到规则四：1000元以上 加1000分");
end
```