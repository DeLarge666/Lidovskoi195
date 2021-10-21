using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class ClickBoost : MonoBehaviour
{
    public Text lvl;
    public string key;
    private int num_lvl = 0;
    public int cell = 0, boost = 0;
    void Start()
    {
        num_lvl = PlayerPrefs.GetInt(key);
        lvl.text = num_lvl.ToString();
        Game.pass_income += boost * num_lvl;
        Game.click_income += boost * num_lvl;
    }
    public void Click_A()
    {
        if (Game.Imoney >= cell && num_lvl < 9)
        {
            num_lvl++;
            PlayerPrefs.SetInt(key, num_lvl);
            lvl.text = num_lvl.ToString();
            Game.Imoney -= cell;
            Game.click_income += boost;
            Game.Tmoney.text = Game.Imoney.ToString();
        }
    }

        public void Click_B()
        {
            if (Game.Imoney >= cell && num_lvl < 9)
            {
                num_lvl++;
                PlayerPrefs.SetInt(key, num_lvl);
                lvl.text = num_lvl.ToString();
                Game.Imoney -= cell;
                Game.pass_income += boost;
                Game.Tmoney.text = Game.Imoney.ToString();
            }
        }
    }
