using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class Game : MonoBehaviour
{
    public GameObject panel;
    public Text T;
    public static Text Tmoney;
    public static int Imoney, click_income, pass_income = 0;
    public float Fmoney = 0;
    private float timer = 5;
    public bool panel_active = false;

    void Start()
    {
        Tmoney = T;
    Imoney = PlayerPrefs.GetInt("Money");
    }

    // Update is called once per frame
    void Update()
    {
        Fmoney += pass_income * Time.deltaTime * 1;
        if (Fmoney >= 1)
        {
            Fmoney--;
            Imoney++;
            Tmoney.text = Imoney.ToString();
        }
    if (timer >0)
        {
            timer -= 1 * Time.deltaTime;
        }
        else
        {
            timer = 5;
            PlayerPrefs.SetInt("Money", Imoney);
     }
    }
    public void Click()
    {
        Imoney += click_income;
        Tmoney.text = Imoney.ToString();
    }    
    public void Active_panel()
    {
        if (panel_active==true)
        {
            panel.SetActive(false);
        }
        else
        {
            panel.SetActive(true);
        }
        panel_active = !panel_active;
    }
    private void OnApplicationQuit()
    {
        PlayerPrefs.Save();
    }
}
