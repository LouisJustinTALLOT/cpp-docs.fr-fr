---
title: Littéral de chaîne | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- string literals
- strings [C++], string literals
ms.assetid: 6d1fc3f8-0d58-4d68-9678-16b4f6dc4766
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 41f1996cd4f4caf24ac08d09b05e636cb09f7eed
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415263"
---
# <a name="string-literal"></a>Littéral de chaîne

La gestion des littéraux de chaîne a été modifiée à partir des Extensions managées pour C++ vers Visual C++.

Dans les Extensions managées pour la conception du langage C++, un littéral de chaîne managé était indiqué en faisant précéder le littéral de chaîne avec un `S`. Exemple :

```
String *ps1 = "hello";
String *ps2 = S"goodbye";
```

Les performances de la charge entre les deux initialisations s’avère pour être non négligeable, en tant que le fichier CIL suivant montre la représentation au travers de **ildasm**:

```
// String *ps1 = "hello";
ldsflda    valuetype $ArrayType$0xd61117dd
     modopt([Microsoft.VisualC]Microsoft.VisualC.IsConstModifier)
     '?A0xbdde7aca.unnamed-global-0'

newobj instance void [mscorlib]System.String::.ctor(int8*)
stloc.0

// String *ps2 = S"goodbye";
ldstr      "goodbye"
stloc.0
```

C’est une économie tout simplement à mémoriser (ou à learning) préfixer une chaîne littérale avec un `S`. Dans la nouvelle syntaxe, la gestion des littéraux de chaîne est rendue transparente, déterminé par le contexte d’utilisation. Le `S` n’a plus besoin de la définir.

Qu’en est-il cas dans lequel nous devons explicitement demander au compilateur d’une interprétation ou une autre ? Dans ce cas, nous appliquons un cast explicite. Exemple :

```
f( safe_cast<String^>("ABC") );
```

En outre, le littéral de chaîne correspond maintenant à un `String` avec une simple conversion plutôt qu’une conversion standard. Bien que ceci peut ne pas sembler beaucoup il modifie la résolution des jeux d’une fonction surchargée qui incluent un `String` et un `const char*` en tant que paramètres formels concurrents. La résolution une fois résolu en un `const char*` instance est désormais signalée comme ambiguë. Exemple :

```
ref struct R {
   void f(const char*);
   void f(String^);
};

int main () {
   R r;
   // old syntax: f( const char* );
   // new syntax: error: ambiguous
   r.f("ABC"); 
}
```

Pourquoi y a-t-il une différence ? Depuis plus d’une instance nommée `f` existe dans le programme, cela nécessite l’algorithme de résolution de surcharge de fonction à appliquer à l’appel. La résolution formelle d’une fonction de surcharge implique trois étapes.

1. La collection des fonctions candidates. Les fonctions candidates sont ces méthodes dans la portée lexicale correspondant au nom de la fonction appelée. Par exemple, depuis `f()` est appelée via une instance de `R`, toutes les fonctions nommées `f` qui ne sont pas un membre de `R` (ou de sa hiérarchie de classe de base) ne sont pas des fonctions candidates. Dans notre exemple, il existe deux fonctions candidates. Voici les deux fonctions membres de `R` nommé `f`. Un appel échoue au cours de cette phase si cet ensemble est vide.

1. L’ensemble des fonctions viables parmi les fonctions candidates. Une viable est une fonction qui peut être appelé avec les arguments spécifiés dans l’appel, étant donné le nombre d’arguments et leurs types. Dans notre exemple, les deux fonctions candidates sont également des fonctions viables. Un appel échoue au cours de cette phase si le jeu de fonctions viables est vide.

1. Sélectionnez la fonction qui représente la meilleure correspondance de l’appel. Pour cela, vous devez classer les conversions appliquées pour transformer les arguments pour le type des paramètres de fonction viable. Il est relativement simple avec une fonction de paramètre unique ; Il devient un peu plus complexe lorsqu’il y a plusieurs paramètres. Un appel échoue au cours de cette phase s’il n’existe aucune meilleure correspondance. Autrement dit, si les conversions nécessaires pour transformer le type de l’argument réel pour le type du paramètre formel sont aussi bonnes. L’appel est signalée comme ambiguë.

Dans les Extensions managées, la résolution de cet appel appelé le `const char*` instance en tant que la meilleure correspondance. Dans la nouvelle syntaxe, les conversions nécessaires pour faire correspondre `"abc"` à `const char*` et `String^` sont désormais équivalents - autrement dit, il est tout aussi bon - et par conséquent, l’appel est signalé comme incorrect - autrement dit, comme ambiguë.

Ceci nous mène à deux questions :

- Quel est le type de l’argument réel, `"abc"`?

- Quel est l’algorithme pour déterminer si une conversion de type est meilleure qu’une autre ?

Le type de littéral de chaîne `"abc"` est `const char[4]` -n’oubliez pas, il existe un caractère de fin null implicit à la fin de chaque chaîne littérale.

L’algorithme permettant de déterminer si une conversion de type est meilleure qu’une autre consiste à placer les conversions de types possibles dans une hiérarchie. Voici ma compréhension de cette hiérarchie - toutes ces conversions sont bien sûr, implicites. À l’aide d’une notation de cast explicite substitue la hiérarchie similaire à la façon dont les parenthèses se substitue à la priorité habituelle des opérateurs d’une expression.

1. Une correspondance exacte est préférable. Étonnamment, pour un argument d’être une correspondance exacte, il est inutile de correspondre exactement au type de paramètre ; Il doit simplement être suffisamment proches. Il s’agit de la clé pour comprendre ce qui se passait dans cet exemple, et comment le langage a changé.

1. Une promotion est préférable à une conversion standard. Par exemple, la promotion un `short int` à un `int` est meilleure que la conversion d’un `int` dans un `double`.

1. Une conversion standard est préférable à une conversion boxing. Par exemple, la conversion une `int` dans un `double` est meilleure que la conversion boxing un `int` dans un `Object`.

1. Une conversion boxing est préférable à une conversion implicite défini par l’utilisateur. Par exemple, le boxing un `int` dans un `Object` est préférable d’appliquer un opérateur de conversion d’un `SmallInt` classe value.

1. Une conversion implicite défini par l’utilisateur est préférable à aucune conversion du tout. Une conversion implicite défini par l’utilisateur est la dernière sortie avant l’erreur (il est à noter que la signature formelle peut contenir un tableau de paramètres ou les points de suspension à cette position).

Par conséquent, ce qui signifie de dire qu’une correspondance exacte n’est pas nécessairement exactement une correspondance ? Par exemple, `const char[4]` ne correspond pas exactement à soit `const char*` ou `String^`, et pourtant l’ambiguïté de notre exemple concerne deux correspondances exactes en conflit !

Une correspondance exacte, il se trouve qu’inclut un nombre de conversions ordinaires. Il existe quatre conversions ordinaires sous ISO-C++ qui peut être appliquée et toujours être considérée comme une correspondance exacte. Trois sont appelés transformations lvalue. Un quatrième type est appelé conversion de qualification. Les trois transformations lvalue sont traitées comme une meilleure correspondance exacte que celles qui nécessitent une conversion de qualification.

Une forme de la transformation de lvalue est la conversion tableau natif de pointeur. C’est ce qu’implique la mise en correspondance un `const char[4]` à `const char*`. Par conséquent, la correspondance de `f("abc")` à `f(const char*)` est une correspondance exacte. Dans les premières versions de notre langage, c’était en fait la meilleure correspondance.

Pour le compilateur signale l’appel comme ambigu, il faut donc que la conversion d’un `const char[4]` à un `String^` également être une correspondance exacte via une conversion ordinaire. Il s’agit de la modification a été introduite dans la nouvelle version de langage. Et c’est pourquoi l’appel est désormais signalée comme ambiguë.

## <a name="see-also"></a>Voir aussi

[Modifications d’ordre général apportées au langage (C++-CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
[String](../windows/string-cpp-component-extensions.md)