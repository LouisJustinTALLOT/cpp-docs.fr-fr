---
title: Source d’organisation du code (modèles C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 50569c5d-0219-4966-9bcf-a8689074ad1d
author: mikeblome
ms.author: mblome
ms.openlocfilehash: ef23b1a12305be9ecf181beb085bb686e81b083b
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939752"
---
# <a name="source-code-organization-c-templates"></a>Organisation du code source (modèles C++)

Lorsque vous définissez un modèle de classe, vous devez organiser le code source, de sorte que les définitions de membres sont visibles par le compilateur lorsqu’il en a besoin.   Vous avez le choix de l’utilisation de la *modèle d’inclusion* ou *instanciation explicite* modèle. Dans le modèle d’inclusion, incluez les définitions de membres dans chaque fichier qui utilise un modèle. Cette approche est la plus simple et fournit une flexibilité maximale en termes de quels types concrets peuvent être utilisés avec votre modèle. Son inconvénient est qu’il peut augmenter le temps de compilation. L’impact peut être significatif si un projet et/ou les fichiers inclus eux-mêmes sont volumineux. Avec l’approche de l’instanciation explicite, le modèle lui-même instancie les classes concrètes ou des membres de classe pour des types spécifiques.  Cette approche peut accélérer les temps de compilation, mais elle limite l’utilisation aux seules classes qui l’implémenteur de modèle a activé à l’avance. En règle générale, nous vous recommandons d’utiliser le modèle d’inclusion, sauf si les temps de compilation deviennent un problème.

## <a name="background"></a>Présentation

Les modèles ne sont pas comme des classes ordinaires en ce sens que le compilateur ne génère pas de code de l’objet pour un modèle ou l’un de ses membres. Il n’y a rien à générer jusqu'à ce que le modèle est instancié avec types concrets. Lorsque le compilateur rencontre une instanciation de modèle comme `MyClass<int> mc;` et aucune classe avec cette signature n’existe encore, il génère une nouvelle classe. Il tente également de générer du code pour toutes les fonctions membres qui sont utilisés. Si ces définitions sont dans un fichier qui n’est pas #included, directement ou indirectement, dans le fichier .cpp qui est en cours de compilation, le compilateur ne les voyez.  Du point de vue du compilateur, ce n’est pas nécessairement une erreur, car les fonctions peuvent être définies dans une autre unité de traduction, dans lequel cas l’éditeur de liens les trouve.  Si l’éditeur de liens ne trouve pas ce code, il déclenche une **externe non résolu** erreur.

## <a name="the-inclusion-model"></a>Le modèle d’inclusion

La façon la plus simple et la plus courante de rendre les définitions de modèle visibles dans une unité de traduction, consiste à placer les définitions dans le fichier d’en-tête.  N’importe quel fichier .cpp qui utilise le modèle a simplement pour #include l’en-tête. Il s’agit de l’approche utilisée dans la bibliothèque Standard.

```cpp
#ifndef MYARRAY
#define MYARRAY
#include <iostream>

template<typename T, size_t N>
class MyArray
{
    T arr[N];
public:
    // Full definitions:
    MyArray(){}
    void Print()
    {
        for (const auto v : arr)
        {
            std::cout << v << " , ";
        }
    }

    T& operator[](int i)
   {
       return arr[i];
   } 
};
#endif
```

Avec cette approche, le compilateur a accès à la définition de modèle complet et pouvez instancier des modèles à la demande pour n’importe quel type. Il est simple et relativement facile à gérer. Toutefois, le modèle d’inclusion a un coût en termes de temps de compilation.   Ce coût peut être significatif dans des programmes volumineux, surtout si l’en-tête du modèle lui-même #includes autres en-têtes. Fichiers chaque .cpp qui #includes l’en-tête obtiendra sa propre copie des modèles de la fonction et toutes les définitions. L’éditeur de liens pourront en général résoudre le problème afin que vous ne finissent pas avec plusieurs définitions pour une fonction, mais il prend le temps de faire ce travail. Dans les programmes plus petits que les temps de compilation supplémentaire ne sont probablement pas significatifs.

## <a name="the-explicit-instantiation-model"></a>Le modèle d’instanciation explicite

Si le modèle d’inclusion n’est pas viable pour votre projet, et vous savez définitivement l’ensemble de types qui sera utilisé pour instancier un modèle, vous pouvez séparer le code du modèle dans un fichier .h et .cpp et dans le fichier .cpp explicitement instancier les modèles. Cela entraîne le code de l’objet doit être généré que le compilateur s’affiche lorsqu’il rencontre des instanciations de l’utilisateur.

Vous créez une instanciation explicite en utilisant le modèle de mot clé suivi de la signature de l’entité que vous souhaitez instancier. Cela peut être un type ou un membre. Si vous instanciez explicitement un type, tous les membres sont instanciés.

```cpp
template MyArray<double, 5>;
```

```cpp
//MyArray.h
#ifndef MYARRAY
#define MYARRAY

template<typename T, size_t N>
class MyArray
{
    T arr[N];
public:
    MyArray();
    void Print();
    T& operator[](int i);
};
#endif

//MyArray.cpp
#include "stdafx.h"
#include <iostream>
#include "MyArray.h"

using namespace std;

template<typename T, size_t N>
MyArray<T,N>::MyArray(){}

template<typename T, size_t N>
void MyArray<T,N>::Print()
{
    for(const auto v : arr)
    {
        cout << v << "'";
    }
    cout << endl;
}

template MyArray<double, 5>;template MyArray<string, 5>;
```

Dans l’exemple précédent, les instanciations explicites se trouvent en bas du fichier .cpp. Un `MyArray` peut être utilisé uniquement pour **double** ou `String` types.

> [!NOTE]
> Dans C ++ 11 les **exporter** mot clé a été déconseillée dans le contexte de définitions de modèle. Dans la pratique, cela a un impact limité, car la plupart des compilateurs jamais pris en charge.
