#UI
## GUI（文字，按钮，输入框，....................）
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class UI : MonoBehaviour
{
    private string test ="这是一个输入框"
    private void OnGUI()//UI回调函数
    {
        GUI.Label(new Rect(10,10,100,50)),"Heelow" ;
    
        //文字UI
    
        // Rect(长,宽，高，尺寸)
        GUI.Button(new Rect(10,60,100,50)),"Logbutton";
        //按钮UI
         bool btnClick = GUI.Button(new Rect(10,60,100,50));
        //设置一个布尔类型判断是否按下按钮
         if(btnClick)
        {
            Debug.Log("按下了按钮“);
        }
        
        test = GUI.TextField(new Rect(10,120,100,50),test);
        //创建一个输入框
    }
}
```
##自动布局：GUILayout
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class UIlLayout : MonoBehaviour
{
    
    private string test = "hellow"

    GUILayout.Button("button 01");
    //创建一个按钮

    test = GUILayout.TextField(test)
    //自动布局，不需要设置，长，宽，高，位置等。
    //了解更多详细查API

}
```
## 添加UI 创建风格
   介绍：GUILayout,是一个自动排版的UI，功能与GUI一样
   先在可视化界面设置好UI
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class UIlLayout : MonoBehaviour
{
    public GUISkin skin;                                //GUI的皮肤样式
    private void OnGUI()
    {
        GUI.skin = this.skin;
        //换上皮肤
    }
  
}
```
## UGUI(unity官方写的UI)
下面是一个文字变色的代码写法
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI//引入命名空间

public class UIlLayout : MonoBehaviour
{
    private Text myText;
    [Header("时间间隔")]
    public float interval = 1;  //时间间隔

    private string headTag = "<color = lime>";

    private string endTag = "</color>";

    private int counter;
    private string originText;

    private void Awake()
    {
        //找到组件
        myText = GetComponent<Text>();
        //获得文本
        originText = myText.
    }
    private void Update()
    {
        timer += Time.deltaTime;
        if(timer>interval)
        {

            counter++; //变色字母的个数
            if(counter > originText.Length>)
            {
                 return
                //插入函数
            }
            myText.text = heaTag + originText.Insert(counter,endTag); 
           if(originText[counter] != ' ')
           {
               timer = 0;
               //空格
           }
            
        }
    }
}
```
![123](D:\daywrite\123.png,"123")
##UI脚本
下面是实现一个技能CD的脚本。
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class UI : MonoBehaviour
{
    public float cd = 3f;//技能冷却时间

    public Image maskImage;//导入图片组件

    private bool beginCD;

    private void Awake()
    {
        maskImage = GetComponent<Image>();
        //获取图片组件
       
    }
    private void update()
    {
         if(Input.GetMouseButtonDown(0)&& ！beginCD)   //按下鼠标左键释放技能
        {
            //设置填充值为1（白色）
            maskImage.fillAmount = 1;

            beginCD = true;
            //开始CD
        }
        if(beginCd)
        {
            maskImage.fillAmount -= Time.deltaTime/cd;
            //转CD，填充值减少
            if(maskImage.fillAmount == 0)
            {
                beginCD = false;
            }
        }
    }   
}