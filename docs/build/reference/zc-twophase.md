---
title: /Zc:twoPhase- (Désactiver la recherche de nom en deux phases)
description: 'Explique comment/Zc : twoPhase : désactive la recherche de nom en deux phases lorsque/permissive-est spécifié.'
ms.date: 12/03/2019
f1_keywords:
- twoPhase
- /Zc:twoPhase
helpviewer_keywords:
- twoPhase
- disable two-phase name lookup
- /Zc:twoPhase
ms.openlocfilehash: 712503d08221d29a61323946008f2f36a467cb31
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234326"
---
# <a name="zctwophase--disable-two-phase-name-lookup"></a>/Zc:twoPhase- (Désactiver la recherche de nom en deux phases)

L’option **/Zc : twoPhase-** , sous **/permissive-**, indique au compilateur d’utiliser le comportement du compilateur Microsoft C++ d’origine non conforme pour analyser et instancier les modèles de classe et les modèles de fonction.

## <a name="syntax"></a>Syntaxe

> **/Zc : twoPhase-**

## <a name="remarks"></a>Notes

Visual Studio 2017 version 15,3 et versions ultérieures : sous [/permissive-](permissive-standards-conformance.md), le compilateur utilise la recherche de nom en deux phases pour la résolution de nom de modèle. Si vous spécifiez également **/Zc : twoPhase-**, le compilateur revient à son modèle de classe non conforme et à son comportement de substitution et à la résolution de nom de modèle de fonction antérieurs. Quand **/permissive-** n’est pas spécifié, le comportement non conforme est le comportement par défaut.

Les fichiers d’en-tête SDK Windows dans la version 10.0.15063.0 (Creators Update ou RS2) et les versions antérieures ne fonctionnent pas en mode conformité. **/Zc : twoPhase-** est requis pour compiler le code de ces versions du kit de développement logiciel (SDK) quand vous utilisez **/permissive-**. Les versions du SDK Windows à partir de la version 10.0.15254.0 (automne Creators Update ou RS3) fonctionnent correctement en mode conformité. Ils n’ont pas besoin de l’option **/Zc : twoPhase-** .

Utilisez **/Zc : twoPhase-** si votre code requiert que l’ancien comportement soit compilé correctement. Envisagez de mettre à jour votre code pour qu’il soit conforme à la norme.

### <a name="compiler-behavior-under-zctwophase-"></a>Comportement du compilateur sous/Zc : twoPhase-

Par défaut, ou dans Visual Studio 2017 version 15,3 et versions ultérieures quand vous spécifiez à la fois **/permissive-** et **/Zc : twoPhase-**, le compilateur utilise ce comportement :

- Il analyse uniquement la déclaration de modèle, l’en-tête de classe et la liste de classes de base. Le corps du modèle est capturé en tant que flux de jetons. Aucun corps de fonction, initialiseurs, arguments par défaut ou arguments noexcept n’est analysé. Le modèle de classe est Pseudo-instancié sur un type provisoire pour valider que les déclarations dans le modèle de classe sont correctes. Considérons ce modèle de classe :

   ```cpp
   template <typename T> class Derived : public Base<T> { ... }
   ```

   La déclaration de modèle, `template <typename T>` , l’en-tête de la classe `class Derived` et la liste de la classe de base `public Base<T>` sont analysées, mais le corps du modèle est capturé en tant que flux de jetons.

- Lors de l’analyse d’un modèle de fonction, le compilateur analyse uniquement la signature de la fonction. Le corps de la fonction n’est jamais analysé. Au lieu de cela, elle est capturée en tant que flux de jetons.

Par conséquent, si le corps du modèle contient des erreurs de syntaxe, mais que le modèle n’est jamais instancié, le compilateur ne diagnostique pas les erreurs.

Un autre effet de ce comportement est la résolution de surcharge. Le comportement non standard se produit en raison de la façon dont le flux de jetons est développé au niveau du site d’instanciation. Les symboles qui n’étaient pas visibles au niveau de la déclaration de modèle peuvent être visibles au point d’instanciation. Cela signifie qu’ils peuvent participer à la résolution de surcharge. Vous pouvez constater que le comportement des modèles change en fonction du code qui n’était pas visible au niveau de la définition du modèle, contrairement à la norme.

Considérez par exemple le code suivant :

```cpp
// zctwophase.cpp
// To test options, compile by using
// cl /EHsc /nologo /W4 zctwophase.cpp
// cl /EHsc /nologo /W4 /permissive- zctwophase.cpp
// cl /EHsc /nologo /W4 /permissive- /Zc:twoPhase- zctwophase.cpp

#include <cstdio>

void func(long) { std::puts("Standard two-phase") ;}

template<typename T> void g(T x)
{
    func(0);
}

void func(int) { std::puts("Microsoft one-phase"); }

int main()
{
    g(6174);
}
```

Voici la sortie lorsque vous utilisez le mode par défaut, le mode de conformité et le mode de conformité avec **/Zc : twoPhase-** options du compilateur :

```cmd
C:\Temp>cl /EHsc /nologo /W4 zctwophase.cpp && zctwophase
zctwophase.cpp
Microsoft one-phase

C:\Temp>cl /EHsc /nologo /W4 /permissive- zctwophase.cpp && zctwophase
zctwophase.cpp
Standard two-phase

C:\Temp>cl /EHsc /nologo /W4 /permissive- /Zc:twoPhase- zctwophase.cpp && zctwophase
zctwophase.cpp
Microsoft one-phase
```

En cas de compilation en mode de conformité sous **/permissive-**, ce programme imprime « `Standard two-phase` », car la deuxième surcharge de `func` n’est pas visible lorsque le compilateur atteint le modèle. Si vous ajoutez **/Zc : twoPhase-**, le programme imprime « `Microsoft one-phase` ». La sortie est la même que si vous ne spécifiez pas **/permissive-**.

Les *noms dépendants* sont des noms qui dépendent d’un paramètre de modèle. Ces noms ont un comportement de recherche qui est également différent sous **/Zc : twoPhase-**. En mode de conformité, les noms dépendants ne sont pas liés au point de la définition du modèle. Au lieu de cela, le compilateur les recherche lorsqu’il instancie le modèle. Pour les appels de fonction avec un nom de fonction dépendant, le nom est lié aux fonctions visibles sur le site d’appel dans la définition de modèle. Des surcharges supplémentaires de la recherche dépendante d’un argument sont ajoutées, à la fois au point de la définition du modèle et au point de l’instanciation du modèle.

La recherche en deux phases se compose de deux parties : la recherche de noms non dépendants lors de la définition du modèle et la recherche de noms dépendants pendant l’instanciation du modèle. Sous **/Zc : twoPhase-**, le compilateur n’effectue pas de recherche dépendante d’un argument, indépendamment de la recherche non qualifiée. Autrement dit, il n’effectue pas de recherche en deux phases, de sorte que les résultats de la résolution de surcharge peuvent être différents.

Voici un autre exemple :

```cpp
// zctwophase1.cpp
// To test options, compile by using
// cl /EHsc /W4 zctwophase1.cpp
// cl /EHsc /W4 /permissive- zctwophase1.cpp
// cl /EHsc /W4 /permissive- /Zc:twoPhase- zctwophase1.cpp

#include <cstdio>

void func(long) { std::puts("func(long)"); }

template <typename T> void tfunc(T t) {
    func(t);
}

void func(int) { std::puts("func(int)"); }

namespace NS {
    struct S {};
    void func(S) { std::puts("NS::func(NS::S)"); }
}

int main() {
    tfunc(1729);
    NS::S s;
    tfunc(s);
}
```

En cas de compilation sans **/permissive-**, ce code imprime :

```Output
func(int)
NS::func(NS::S)
```

En cas de compilation avec **/permissive-**, mais sans **/Zc : twoPhase-**, ce code imprime :

```Output
func(long)
NS::func(NS::S)
```

En cas de compilation avec **/permissive-** et **/Zc : twoPhase-**, ce code imprime :

```Output
func(int)
NS::func(NS::S)
```

En mode conformité sous **/permissive-**, l’appel est `tfunc(1729)` résolu en `void func(long)` surcharge. Elle ne se résout pas en `void func(int)` surcharge, comme sous **/Zc : twoPhase-**. Cela est dû au fait que la non qualifiée `func(int)` est déclarée après la définition du modèle, et qu’elle n’est pas trouvée par le biais d’une recherche dépendante d’un argument. Mais `void func(S)` participe à une recherche dépendante d’un argument. elle est donc ajoutée à la surcharge définie pour l’appel `tfunc(s)` , même si elle est déclarée après la fonction de modèle.

### <a name="update-your-code-for-two-phase-conformance"></a>Mettre à jour votre code pour la conformité en deux phases

Les versions antérieures du compilateur n’ont pas besoin des mots clés **`template`** et **`typename`** partout où la norme C++ les requiert. Ces mots clés sont nécessaires dans certaines positions pour lever l’ambiguïté selon laquelle les compilateurs doivent analyser un nom dépendant pendant la première phase de la recherche. Par exemple :

`T::Foo<a || b>(c);`

Un compilateur conforme `Foo` est analysé en tant que variable dans la portée de `T` , ce qui signifie que ce code est une expression or logique avec `T::foo < a` comme opérande gauche et `b > (c)` comme opérande droit. Si vous souhaitez utiliser `Foo` comme modèle de fonction, vous devez indiquer qu’il s’agit d’un modèle en ajoutant le **`template`** mot clé :

`T::template Foo<a || b>(c);`

Dans les versions de Visual Studio 2017 version 15,3 et ultérieures, quand **/permissive-** et **/Zc : twoPhase** sont spécifiés, le compilateur autorise ce code sans le **`template`** mot clé. Il interprète le code comme un appel à un modèle de fonction avec un argument de `a || b` , car il analyse uniquement les modèles de manière limitée. Le code ci-dessus n’est pas analysé du tout au cours de la première phase. Pendant la deuxième phase, il y a suffisamment de contexte pour dire que `T::Foo` est un modèle plutôt qu’une variable, si bien que le compilateur n’impose pas l’utilisation du mot clé.

Ce comportement peut également être observé en éliminant le mot clé **`typename`** avant les noms dans les corps de modèle de fonction, les initialiseurs, les arguments par défaut et les arguments noexcept. Par exemple :

```cpp
template<typename T>
typename T::TYPE func(typename T::TYPE*)
{
    /* typename */ T::TYPE i;
}
```

Si vous n’utilisez pas le mot clé **`typename`** dans le corps de la fonction, ce code est compilé sous **/permissive-/Zc : twoPhase-**, mais pas sous **/permissive-** seul. Le **`typename`** mot clé est requis pour indiquer que le `TYPE` est dépendant de. Étant donné que le corps n’est pas analysé sous **/Zc : twoPhase-**, le compilateur demandé n’requiert le mot clé. En mode de conformité **/permissive-** , le code sans le **`typename`** mot clé génère des erreurs. Pour migrer votre code en conformité dans Visual Studio 2017 version 15,3 et ultérieur, insérez le **`typename`** mot clé dans lequel il est manquant.

De même, considérez cet exemple de code :

```cpp
template<typename T>
typename T::template X<T>::TYPE func(typename T::TYPE)
{
    typename T::/* template */ X<T>::TYPE i;
}
```

Sous **/permissive-/Zc : twoPhase-** et dans les compilateurs plus anciens, le compilateur requiert uniquement le **`template`** mot clé sur la ligne 2. En mode conformité, le compilateur requiert désormais également le **`template`** mot clé sur la ligne 4 pour indiquer que `T::X<T>` est un modèle. Recherchez le code qui ne contient pas ce mot clé et fournissez-le pour que votre code soit conforme à la norme.

Pour plus d’informations sur les problèmes de conformité, consultez [améliorations de la conformité de C++ dans Visual Studio](../../overview/cpp-conformance-improvements.md) et [comportement non standard](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Modifiez la propriété **options supplémentaires** pour inclure **/Zc : twoPhase-** , puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](zc-conformance.md)
