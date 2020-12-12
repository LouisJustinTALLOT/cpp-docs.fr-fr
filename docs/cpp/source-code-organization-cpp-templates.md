---
description: 'En savoir plus sur : organisation du code source (modèles C++)'
title: Organisation du code source (modèles C++)
ms.date: 04/22/2019
ms.assetid: 50569c5d-0219-4966-9bcf-a8689074ad1d
ms.openlocfilehash: 72777c550cf36fd635432a8ce840af92f0a3f893
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113868"
---
# <a name="source-code-organization-c-templates"></a>Organisation du code source (modèles C++)

Lorsque vous définissez un modèle de classe, vous devez organiser le code source de sorte que les définitions de membres soient visibles par le compilateur en cas de besoin. Vous avez le choix d’utiliser le *modèle d’inclusion* ou le modèle d’*instanciation explicite*. Dans le modèle d’inclusion, vous incluez les définitions de membre dans chaque fichier qui utilise un modèle. Cette approche est la plus simple et offre une flexibilité maximale en termes de types concrets compatibles avec votre modèle. Son inconvénient est qu’il peut augmenter le délai de compilation. L’impact peut être significatif si un projet et/ou les fichiers inclus sont eux-mêmes volumineux. Avec l’instanciation explicite, le modèle lui-même instancie les classes ou les membres de classe concrets pour des types spécifiques.  Cette approche peut accélérer le délai de compilation, mais elle limite l’utilisation aux seules classes que l’implémenteur de modèle a activées à l’avance. En règle générale, nous vous recommandons d’utiliser le modèle d’inclusion, sauf si le délai de compilation pose problème.

## <a name="background"></a>Arrière-plan

Les modèles ne constituent pas des classes ordinaires, en ce sens que le compilateur ne génère pas le code de l’objet pour un modèle ou l’un de ses membres. Il n’y a rien à générer tant que le modèle n’est pas instancié avec des types concrets. Lorsque le compilateur rencontre une instanciation de modèle comme `MyClass<int> mc;` et qu’il n’existe encore aucune classe avec cette signature, il génère une nouvelle classe. Il tente également de générer le code des fonctions d’un membre qui sont utilisées. Si ces définitions figurent dans un fichier qui n’est pas inclus, directement ou indirectement, dans le fichier .cpp en cours de compilation, le compilateur ne peut pas les détecter.  Du point de vue du compilateur, il ne s’agit pas nécessairement d’une erreur car les fonctions peuvent être définies dans une autre unité de traduction et, dans ce cas, l’éditeur de liens les identifie.  Si l’éditeur de liens ne trouve pas ce code, il déclenche une erreur *externe non résolue*.

## <a name="the-inclusion-model"></a>Le modèle d’inclusion

La façon la plus simple et la plus courante d’afficher les définitions de modèle dans une unité de traduction consiste à placer les définitions dans le fichier d’en-tête.  Tout fichier .cpp qui utilise le modèle doit simplement inclure l’en-tête. Il s’agit de l’approche utilisée dans la bibliothèque standard.

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

Avec cette approche, le compilateur a accès à la définition de modèle complète et peut instancier des modèles à la demande pour n’importe quel type. C’est une solution simple et relativement facile à gérer. Mais le modèle d’inclusion présente un certain coût en termes de délai de compilation. Ce coût peut être significatif dans des programmes volumineux, surtout si l’en-tête du modèle lui-même inclut d’autres en-têtes. Chaque *`.cpp`* fichier qui #includes l’en-tête obtiendra sa propre copie des modèles de fonction et de toutes les définitions. L’éditeur de liens pourra généralement résoudre le problème pour éviter la création de plusieurs définitions pour une même fonction, mais cette opération prend du temps. Dans les programmes plus petits, ce délai de compilation supplémentaire sera sans doute marginal.

## <a name="the-explicit-instantiation-model"></a>Le modèle d’instanciation explicite

Si le modèle d’inclusion n’est pas viable pour votre projet et que vous connaissez définitivement l’ensemble des types qui seront utilisés pour instancier un modèle, vous pouvez séparer le code du modèle dans un *`.h`* *`.cpp`* fichier et, et dans le *`.cpp`* fichier instancier explicitement les modèles. Ainsi, le code de l’objet sera généré et le compilateur pourra le voir lorsqu’il rencontre des instanciations de l’utilisateur.

Vous créez une instanciation explicite en utilisant le modèle de mot clé suivi de la signature de l’entité que vous souhaitez instancier. Il peut s’agir d’un type ou d’un membre. Si vous instanciez explicitement un type, tous les membres sont instanciés.

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
#include <iostream>
#include "MyArray.h"

using namespace std;

template<typename T, size_t N>
MyArray<T,N>::MyArray(){}

template<typename T, size_t N>
void MyArray<T,N>::Print()
{
    for (const auto v : arr)
    {
        cout << v << "'";
    }
    cout << endl;
}

template MyArray<double, 5>;template MyArray<string, 5>;
```

Dans l’exemple précédent, les instanciations explicites se trouvent en bas du fichier .cpp. Un `MyArray` peut être utilisé uniquement pour **`double`** les `String` types ou.

> [!NOTE]
> En C++ 11, le **`export`** mot clé était déconseillé dans le contexte des définitions de modèle. Dans la pratique, cela a un impact limité car la plupart des compilateurs ne l’ont jamais pris en charge.
