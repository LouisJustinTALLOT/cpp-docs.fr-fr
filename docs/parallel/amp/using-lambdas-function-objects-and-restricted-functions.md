---
title: Utilisation de fonctions lambda, d'objets de fonctions et de fonctions restreintes
ms.date: 11/04/2016
ms.assetid: 25346cc9-869d-4ada-aad3-e2228cad3d6c
ms.openlocfilehash: 0c72ae6f600fe73405481e34ab05b60f163e44d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405324"
---
# <a name="using-lambdas-function-objects-and-restricted-functions"></a>Utilisation de fonctions lambda, d'objets de fonctions et de fonctions restreintes

Le C++ code AMP que vous souhaitez exécuter sur l’accélérateur est spécifié en tant qu’argument dans un appel à la [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) (méthode). Vous pouvez fournir une expression lambda ou un objet de fonction (functor) en tant qu’argument. En outre, l’objet d’expression ou une fonction lambda peut appeler une fonction restreinte C++ AMP. Cette rubrique utilise un algorithme d’addition de tableau pour illustrer les expressions lambda, les objets de fonction et les fonctions restreintes. L’exemple suivant montre l’algorithme sans code C++ AMP. Tableaux à deux dimensions de 1 de longueur égale sont créés. Les éléments entiers correspondants sont ajoutés et stockés dans un troisième tableau 1D. C++ AMP n’est pas utilisé.

```cpp
void CpuMethod() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    for (int idx = 0; idx <5; idx++)
    {
        sumCPP[idx] = aCPP[idx] + bCPP[idx];
    }

    for (int idx = 0; idx <5; idx++)
    {
        std::cout <<sumCPP[idx] <<"\n";
    }
}
```

## <a name="lambda-expression"></a>Expression lambda

À l’aide d’une expression lambda est le moyen le plus direct d’utiliser C++ AMP pour réécrire le code.

```cpp
void AddArraysWithLambda() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    array_view<const int, 1> a(5, aCPP);

    array_view<const int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp)
        {
             sum[idx] = a[idx] + b[idx];
        });

    for (int i = 0; i <5; i++) {
        std::cout <<sum[i] <<"\n";
    }
}
```

L’expression lambda doit inclure un paramètre d’indexation, ainsi `restrict(amp)`. Dans l’exemple, le [array_view](../../parallel/amp/reference/array-view-class.md) `sum` objet a le rang 1. Par conséquent, le paramètre de l’instruction lambda est un [index](../../parallel/amp/reference/index-class.md) objet ayant le rang 1. Lors de l’exécution, l’expression lambda est exécutée une fois pour chaque élément dans le [array_view](../../parallel/amp/reference/array-view-class.md) objet. Pour plus d’informations, consultez [syntaxe d’Expression Lambda](../../cpp/lambda-expression-syntax.md).

## <a name="function-object"></a>Objet de function

Vous pouvez factoriser le code d’accélérateur dans un objet de fonction.

```cpp
class AdditionFunctionObject
{
public:
    AdditionFunctionObject(const array_view<int, 1>& a,
    const array_view<int, 1>& b,
    const array_view<int, 1>& sum)
    : a(a), b(b), sum(sum)
    {
    }

    void operator()(index<1> idx) restrict(amp)
    {
        sum[idx] = a[idx] + b[idx];
    }

private:
    array_view<int, 1> a;
    array_view<int, 1> b;
    array_view<int, 1> sum;
};

void AddArraysWithFunctionObject() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    array_view<const int, 1> a(5, aCPP);

    array_view<const int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

    parallel_for_each(
        sum.extent,
        AdditionFunctionObject(a, b, sum));

    for (int i = 0; i <5; i++) {
        std::cout <<sum[i] <<"\n";
    }
}
```

L’objet de fonction doit inclure un constructeur et doit inclure une surcharge de l’opérateur d’appel de fonction. L’opérateur d’appel de fonction doit inclure un paramètre d’indexation. Une instance de l’objet de fonction est passée comme deuxième argument à la [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) (méthode). Dans cet exemple, trois [array_view](../../parallel/amp/reference/array-view-class.md) objets sont passés au constructeur d’objet de fonction. Le [array_view](../../parallel/amp/reference/array-view-class.md) objet `sum` a le rang 1. Par conséquent, le paramètre de l’opérateur d’appel de fonction est un [index](../../parallel/amp/reference/index-class.md) objet ayant le rang 1. Lors de l’exécution, la fonction est exécutée une fois pour chaque élément dans le [array_view](../../parallel/amp/reference/array-view-class.md) objet. Pour plus d’informations, consultez [appel de fonction](../../cpp/function-call-cpp.md) et [des objets de fonction dans la bibliothèque Standard C++](../../standard-library/function-objects-in-the-stl.md).

## <a name="c-amp-restricted-function"></a>Fonction restreinte à AMP de C++

Vous pouvez davantage factoriser le code de l’accélérateur en créant une fonction restreinte et en appelant à partir d’une expression lambda ou un objet de fonction. L’exemple de code suivant montre comment appeler une fonction restreinte à partir d’une expression lambda.

```cpp
void AddElementsWithRestrictedFunction(index<1> idx, array_view<int, 1> sum, array_view<int, 1> a, array_view<int, 1> b) restrict(amp)
{
    sum[idx] = a[idx] + b[idx];
}

void AddArraysWithFunction() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    array_view<int, 1> a(5, aCPP);

    array_view<int, 1> b(5, bCPP);

    array_view<int, 1> sum(5, sumCPP);

    sum.discard_data();

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp)
        {
            AddElementsWithRestrictedFunction(idx, sum, a, b);
        });

    for (int i = 0; i <5; i++) {
        std::cout <<sum[i] <<"\n";
    }
}
```

La fonction restreinte doit inclure `restrict(amp)` et être conformes aux restrictions décrites dans [restreindre (C++ AMP)](../../cpp/restrict-cpp-amp.md).

## <a name="see-also"></a>Voir aussi

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Syntaxe d’expression lambda](../../cpp/lambda-expression-syntax.md)<br/>
[Appel de fonction ](../../cpp/function-call-cpp.md)<br/>
[Objets de fonction dans la bibliothèque standard C++](../../standard-library/function-objects-in-the-stl.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)
