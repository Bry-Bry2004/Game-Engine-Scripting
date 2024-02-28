using System.Collections;
using System.Collections.Generic;
using UnityEditor;
using UnityEditor.UI;
using UnityEngine;


public class Flower : MonoBehaviour
{
    
    public float nectarProductionRate = 5f;
    public Color nectarColor = Color.yellow;
    public Color defaultColor = Color.white;

    private float nectar = 0f;
    private float counter = 0f;
    private bool isProducingNectar = false;
    private bool hasNectar = false;
    private Renderer flowerRenderer;

    // Start is called before the first frame update
    void Start()
    {
        StartCoroutine(ProduceNectar());
        //Starting nectar production

        flowerRenderer = GetComponent<Renderer>();
    }

    // Update is called once per frame
    void Update()
    {
        //Nectar inspectionnn
        if (!hasNectar)
        {
            counter += Time.deltaTime;

            if (counter >= nectarProductionRate)
            {
                counter = 0f;
                nectar += nectarProductionRate;
                Debug.Log("Nectar produced! Current nectar level: " + nectar);
                ChangeColor(nectarColor);
            }
        }
    }

    IEnumerator ProduceNectar()
    {
        isProducingNectar = true;

        while (isProducingNectar)
        {
            yield return new WaitForSeconds(5f);
            nectar += nectarProductionRate;
            Debug.Log("Nectar produced! Current nectar level: " + nectar);

            if(nectar <= 0f)
            {
                hasNectar = false;
                ChangeColor(defaultColor);
            }
        }
    }

    public bool HasNectar()
    {
        return hasNectar;
    }

    public bool TakeNectar()
    {
        if(hasNectar)
        {
            hasNectar = false;
            counter = 0f;
            ChangeColor(defaultColor);
            return true;
        }
        else
        {
            return false;
        }
    }

    private void ChangeColor(Color color)
    {
        flowerRenderer.material.color = color;
    }

    public float GetNectarLevel()
    {
        return nectar;
    }
}
