Небольшой скрипт или скорее просто пример. Допустим, при взаимодействии игровых объектов, нужно чтобы была выполнена та или иная функция, выбранная рандомно. И тут возникает вопрос, как создать массив из различных функций, а затем выполнить какую-либо по номеру индекса? В общем, как и в любом обычном массиве. Конечно, можно обойтись, например, используя switch, и переключаться между нужными функциями. Тем не менее, возможность создавать массивы из самих функций скрипта, полагаем будет не лишнем. Конструкция достаточно простоя, поэтому берем и пользуемся, предоставленным ниже примером. 
Собственно пример:
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour {

	private System.Action myUpdate = () => {}; 
	private System.Action[] actions;

	void Start()
	{
		actions = new System.Action[]{FunctionA, FunctionB, FunctionC};
	}

	public void FunctionUpdate(int index)
	{
		myUpdate = actions[index];
		myUpdate();
	}

	void FunctionA()
	{
		Debug.Log("Function A");
	}

	void FunctionB()
	{
		Debug.Log("Function B");
	}

	void FunctionC()
	{
		Debug.Log("Function C");
	}
}

Если мы хотим выполнить рандомную функцию, сделать это можно так:

FunctionUpdate(Random.Range(0, actions.Length));