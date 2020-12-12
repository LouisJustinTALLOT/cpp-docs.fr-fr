---
description: 'En savoir plus sur : utilisation des expressions lambda, des objets de fonction et des fonctions restreintes'
title: Utilisation de fonctions lambda, d'objets de fonctions et de fonctions restreintes
ms.date: 11/04/2016
ms.assetid: 25346cc9-869d-4ada-aad3-e2228cad3d6c
ms.openlocfilehash: bef02f30b5d5b5f11b8051c7a596ac0a141eef0a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314449"
---
# <a name="using-lambdas-function-objects-and-restricted-functions"></a>Utilisation de fonctions lambda, d'objets de fonctions et de fonctions restreintes

Le code C++ AMP que vous souhaitez exécuter sur l’accélérateur est spécifié en tant qu’argument dans un appel à la méthode [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) . Vous pouvez fournir une expression lambda ou un objet de fonction (functor) comme cet argument. En outre, l’expression lambda ou l’objet de fonction peut appeler une fonction restreinte par C++ AMP. Cette rubrique utilise un algorithme d’ajout de tableau pour illustrer les expressions lambda, les objets de fonction et les fonctions restreintes. L’exemple suivant illustre l’algorithme sans C++ AMP code. Des tableaux 2 1 dimensionnels de longueur égale sont créés. Les éléments entiers correspondants sont ajoutés et stockés dans un troisième tableau unidimensionnel. C++ AMP n’est pas utilisé.

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

L’utilisation d’une expression lambda est le moyen le plus direct d’utiliser C++ AMP pour réécrire le code.

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

L’expression lambda doit inclure un paramètre d’indexation et doit inclure `restrict(amp)` . Dans l’exemple, l’objet [array_view](../../parallel/amp/reference/array-view-class.md) `sum` a le rang 1. Par conséquent, le paramètre de l’instruction lambda est un objet [index](../../parallel/amp/reference/index-class.md) qui a le rang 1. Lors de l’exécution, l’expression lambda est exécutée une fois pour chaque élément de l’objet [array_view](../../parallel/amp/reference/array-view-class.md) . Pour plus d’informations, consultez [syntaxe d’expression lambda](../../cpp/lambda-expression-syntax.md).

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

L’objet de fonction doit inclure un constructeur et doit inclure une surcharge de l’opérateur d’appel de fonction. L’opérateur d’appel de fonction doit inclure un paramètre d’indexation. Une instance de l’objet de fonction est passée comme deuxième argument à la méthode [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) . Dans cet exemple, trois objets [array_view](../../parallel/amp/reference/array-view-class.md) sont passés au constructeur d’objet de fonction. Le rang de l’objet [array_view](../../parallel/amp/reference/array-view-class.md) est égal à `sum` 1. Par conséquent, le paramètre de l’opérateur d’appel de fonction est un objet [index](../../parallel/amp/reference/index-class.md) qui a le rang 1. Lors de l’exécution, la fonction est exécutée une fois pour chaque élément de l’objet [array_view](../../parallel/amp/reference/array-view-class.md) . Pour plus d’informations, consultez [appel de fonction](../../cpp/function-call-cpp.md) et [objets de fonction dans la bibliothèque standard C++](../../standard-library/function-objects-in-the-stl.md).

## <a name="c-amp-restricted-function"></a>Fonction C++ AMP-Restricted

Vous pouvez mieux factoriser le code d’accélérateur en créant une fonction restreinte et en l’appelant à partir d’une expression lambda ou d’un objet de fonction. L’exemple de code suivant montre comment appeler une fonction restreinte à partir d’une expression lambda.

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

La fonction restreinte doit inclure `restrict(amp)` et respecter les restrictions décrites dans [restreindre (C++ amp)](../../cpp/restrict-cpp-amp.md).

## <a name="see-also"></a>Voir aussi

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Syntaxe d’expression lambda](../../cpp/lambda-expression-syntax.md)<br/>
[Appel de fonction](../../cpp/function-call-cpp.md)<br/>
[Objets de fonction dans la bibliothèque C++ standard](../../standard-library/function-objects-in-the-stl.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)
