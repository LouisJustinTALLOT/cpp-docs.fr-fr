---
title: /Zc:twoPhase-(désactiver la recherche de nom en deux phases) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- twoPhase
- /Zc:twoPhase
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
dev_langs:
- C++
helpviewer_keywords:
- twoPhase
- disable two-phase name lookup
- /Zc:twoPhase
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30647ab07984c393b10d7c0fb74d0e2be35cdf26
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723292"
---
# <a name="zctwophase--disable-two-phase-name-lookup"></a>/Zc:twoPhase-(désactiver la recherche de nom en deux phases)

Lorsque le **/Zc:twoPhase-** est spécifiée, le compilateur analyse et instancie les modèles de classe et des modèles de fonction de la même façon que les versions de Visual Studio antérieures à Visual Studio 2017 version 15.3 non conforme.

## <a name="syntax"></a>Syntaxe

> **/Zc:twoPhase-**

## <a name="remarks"></a>Notes

Dans Visual Studio 2017 version 15.3 et versions ultérieures, par défaut, le compilateur utilise la recherche de nom en deux phases pour la résolution de nom de modèle. Si **/Zc:twoPhase-** est spécifié, le compilateur reprend son précédent non conformes classe modèle et la fonction de modèle nom résolution et la substitution de comportement.

Le **/Zc:twoPhase-** option permettant d’activer un comportement non conforme n’est pas définie par défaut. Le [/ permissive-](permissive-standards-conformance.md) option définit implicitement le comportement du compilateur de recherche en deux phases conforme, mais elle peut être substituée à l’aide de **/Zc:twoPhase-**.

Les fichiers d’en-tête Windows SDK dans la version 10.0.15063.0 (Creators Update ou Redstone 2) et les versions antérieures ne fonctionnent pas correctement en mode de mise en conformité. Vous devez utiliser **/Zc:twoPhase-** pour compiler le code pour ces versions du Kit de développement logiciel lorsque vous utilisez Visual Studio 2017 version 15.3 et versions ultérieures. Les versions du SDK Windows depuis la version 10.0.15254.0 (Redstone 3 ou Fall Creators Update) fonctionne correctement en mode de conformité et ne nécessitent pas la **/Zc:twoPhase-** option.

Utilisez **/Zc:twoPhase-** si votre code requiert l’ancien comportement pour une compilation correcte. Sérieusement envisager la mise à jour votre code pour se conformer à la norme.

### <a name="compiler-behavior-under-zctwophase-"></a>Comportement du compilateur sous /Zc:twoPhase-

Dans les versions du compilateur avant Visual Studio 2017 version 15.3 et à quel moment **/Zc:twoPhase-** est spécifié, le compilateur utilise ce comportement :

- Il analyse uniquement la déclaration de modèle, le titre de la classe et la liste de classe de base. Le corps du modèle est capturé en tant que jeton flux. Aucun corps de fonction, les initialiseurs, les arguments par défaut ou les arguments de noexcept ne sont analysés. Le modèle de classe est instanciée pseudo sur un type provisoire pour valider que les déclarations dans le modèle de classe sont correctes. Prenez en compte ce modèle de classe :

   ```cpp
   template <typename T> class Derived : public Base<T> { ... }
   ```

   La déclaration de modèle, `template <typename T`>, le titre de la classe `class Derived`et la liste de classe de base `public Base<T>` sont analysés, mais le corps du modèle est capturé en tant que jeton flux.

- Lors de l’analyse un modèle de fonction, le compilateur analyse uniquement la signature de fonction. Le corps de fonction n’est jamais analysé. Au lieu de cela, il est capturé en tant que jeton flux.

Par conséquent, si le corps du modèle comporte des erreurs de syntaxe et le modèle n’est jamais instancié, les erreurs ne sont jamais diagnostiqués.

Un autre effet de ce comportement est dans la résolution de surcharge. En raison de la façon dont le flux de jeton est développé sur le site de l’instanciation, les symboles qui n’étaient pas visibles dans la déclaration de modèle peuvent être visibles au moment de l’instanciation et participer à la résolution de surcharge. Cela peut entraîner des modèles pour modifier le comportement en fonction de code qui n’était pas visible lorsque le modèle a été défini, contrairement à la norme.

Par exemple, prenons le code suivant :

```cpp
#include <cstdio>

void func(void*) { std::puts("The call resolves to void*") ;}

template<typename T> void g(T x)
{
    func(0);
}

void func(int) { std::puts("The call resolves to int"); }

int main()
{
    g(3.14);
}
```

Lors de la compilation sous **/Zc:twoPhase-**, ce programme imprime « l’appel correspond à int ». Dans le mode de conformité sous **/ permissive-**, ce programme imprime « l’appel est résolu en void * », car la deuxième surcharge de `func` n’est pas visible lorsque le compilateur rencontre le modèle.

*Noms dépendants*, les noms qui dépendent d’un paramètre de modèle, ont un comportement de recherche qui est également différent sous **/Zc:twoPhase-**. Dans le mode de conformité, les noms dépendants ne sont pas liés au moment de la définition du modèle. Au lieu de cela, ces noms sont recherchés quand le modèle est instancié. Pour les appels de fonction avec un nom de fonction dépendant, le nom est lié à l’ensemble de fonctions qui sont visibles au moment de l’appel de la définition du modèle, comme indiqué ci-dessus. Des surcharges supplémentaires à partir de la recherche dépendante d’argument sont ajoutés à la fois le point de la définition du modèle et le point d’où le modèle est instancié. Les deux phases de recherche en deux phases sont la recherche pour les noms non dépendants au moment de la définition de modèle et la recherche de noms dépendants au moment de l’instanciation du modèle. Sous **/Zc:twoPhase-**, le compilateur ne recherche dépendante d’un argument séparément à partir de la recherche ordinaire et non qualifié (autrement dit, il ne recherche en deux phases), les résultats de la résolution de surcharge peut donc être différentes.

Voici un autre exemple :

```cpp
// zctwophase1.cpp
// Compile by using
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

Lors de la compilation sans **/Zc:twoPhase-**, cela imprime

```Output
func(long)
NS::func(NS::S)
```

Lors de la compilation avec **/Zc:twoPhase-**, cela imprime

```Output
func(int)
NS::func(NS::S)
```

Dans le mode de conformité sous **/ permissive-**, l’appel `tfunc(1729)` se résout en la `void func(long)` de surcharge, pas `void func(int)` surcharger comme sous **/Zc:twoPhase-**, car le non qualifié `func(int)` est déclarée après la définition du modèle et pas identifiés par la recherche dépendante d’un argument. Mais `void func(S)` participe recherche dépendante d’un argument, elle est ajoutée à la surcharge défini pour l’appel `tfunc(s)` même si elle est déclarée après la fonction de modèle.

### <a name="update-your-code-for-two-phase-conformance"></a>Mettre à jour votre code pour la conformité en deux phases

Les versions antérieures du compilateur ne nécessitent pas les mots clés `template` et `typename` partout où la norme C++ en a besoin. Ces mots clés sont nécessaires dans certaines positions pour lever l’ambiguïté comment compilateurs doivent analyser un nom dépendant pendant la première phase de recherche. Exemple :

`T::Foo<a || b>(c);`

Analyse d’un compilateur conforme `Foo` en tant que variable dans la portée du `T`, ce qui signifie que ce code est un opérateur logique- ou expression avec `T::foo < a` en tant que l’opérande de gauche et `b > (c)` comme opérande de droite. Si vous souhaitez utiliser `Foo` comme un modèle de fonction, vous devez indiquer qu’il s’agit un modèle en ajoutant le `template` mot clé :

`T::template Foo<a || b>(c);`

Dans les versions antérieures de Visual Studio 2017 version 15.3 et à quel moment **/Zc:twoPhase-** est spécifié, le compilateur autorise ce code sans le `template` mot clé et l’interprète comme un appel à un modèle de fonction avec un argument de `a || b`, car il analyse les modèles de manière très limitée. Le code ci-dessus n’est pas analysé du tout dans la première phase. Pendant la deuxième phase, il existe suffisamment de contexte pour déterminer que `T::Foo` est un modèle, et non une variable pour le compilateur n’applique pas l’utilisation du mot-clé.

Ce comportement peut également être affichée en éliminant le mot clé `typename` avant les noms dans le corps de modèle de fonction, les initialiseurs, les arguments par défaut et les arguments de noexcept. Exemple :

```cpp
template<typename T>
typename T::TYPE func(typename T::TYPE*)
{
    /* typename */ T::TYPE i;
}
```

Si vous n’utilisez pas le mot clé `typename` dans le corps de fonction, ce code est compilé sous **/Zc:twoPhase-**, mais pas sous **/ permissive-**. Le `typename` mot clé est nécessaire pour indiquer que le `TYPE` est dépendante. Étant donné que le corps n’est pas analysé sous **/Zc:twoPhase-**, le compilateur does't nécessitent le mot clé. Dans **/ permissive-** mode de conformité, de code sans le `typename` mot clé génère des erreurs. Pour migrer votre code vers Visual Studio 2017 version 15.3 et au-delà, insérer le `typename` mot clé où il est manquant.

De même, envisagez de cet exemple de code :

```cpp
template<typename T>
typename T::template X<T>::TYPE func(typename T::TYPE)
{
    typename T::/* template */ X<T>::TYPE i;
}
```

Sous **/Zc:twoPhase-** et dans les compilateurs plus anciens, le compilateur nécessite seulement le `template` mot clé sur la ligne 2. Par défaut et dans le mode de conformité, le compilateur également requiert désormais le `template` mot clé sur la ligne 4 pour indiquer que `T::X<T>` est un modèle. Recherchez le code auquel il manque ce mot clé et lui fournir pour rendre votre code est conforme à la norme.

Pour plus d’informations sur les problèmes de conformité, consultez [améliorations de la conformité de C++ dans Visual Studio](../../cpp-conformance-improvements-2017.md) et [comportement non standard](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Modifier le **des Options supplémentaires** propriété à inclure **/Zc:twoPhase-** , puis **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](../../build/reference/zc-conformance.md)<br/>
