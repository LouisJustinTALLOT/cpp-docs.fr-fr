---
description: 'En savoir plus sur : `__declspec`'
title: __declspec
ms.date: 03/21/2019
f1_keywords:
- __declspec_cpp
- __declspec
- _declspec
helpviewer_keywords:
- __declspec keyword [C++]
ms.openlocfilehash: d0567c522e0e21f70b9ed8acfa428c3374fd09f6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339538"
---
# `__declspec`

**Spécifique à Microsoft**

La syntaxe d’attribut étendu pour la spécification des informations de classe de stockage utilise le **`__declspec`** mot clé, qui spécifie qu’une instance d’un type donné doit être stockée avec un attribut de classe de stockage spécifique à Microsoft ci-dessous. Les **`static`** Mots clés et sont des exemples d’autres modificateurs de classe de stockage **`extern`** . Toutefois, ces mots clés font partie de la spécification ANSI des langages C et C++ et, en tant que tels, ne sont pas couverts par la syntaxe à attributs étendus. La syntaxe à attributs étendus simplifie et normalise les extensions spécifiques à Microsoft pour les langages C et C++.

## <a name="grammar"></a>Grammaire

*`decl-specifier`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__declspec (`**  *`extended-decl-modifier-seq`*  **`)`**

*`extended-decl-modifier-seq`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`extended-decl-modifier`*<sub>possibilité</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`extended-decl-modifier`* *`extended-decl-modifier-seq`*

*`extended-decl-modifier`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`align(`***nombre***`)`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`allocate("`***segname***`")`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`allocator`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`appdomain`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`code_seg("`***segname***`")`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`deprecated`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`dllimport`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`dllexport`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`jitintrinsic`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`naked`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`noalias`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`noinline`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`noreturn`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`nothrow`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`novtable`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`process`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`property(`**{- **`get=`** _Func-Name_ &#124; **`,put=`** _put-Func-Name_ }**`)`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`restrict`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`safebuffers`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`selectany`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`spectre(nomitigation)`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`thread`**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`uuid("`***ComObjectGUID***`")`**

Un espace blanc sépare la séquence de modificateur de déclaration. Des exemples sont donnés dans des sections ultérieures.

La grammaire des attributs étendus prend en charge les attributs de classe de stockage spécifiques à Microsoft suivants :,,,,,,,,,, [`align`](../cpp/align-cpp.md) [`allocate`](../cpp/allocate.md) [`allocator`](../cpp/allocator.md) [`appdomain`](../cpp/appdomain.md) [`code_seg`](../cpp/code-seg-declspec.md) [`deprecated`](../cpp/deprecated-cpp.md) [`dllexport`](../cpp/dllexport-dllimport.md) [`dllimport`](../cpp/dllexport-dllimport.md) [`jitintrinsic`](../cpp/jitintrinsic.md) [`naked`](../cpp/naked-cpp.md) [`noalias`](../cpp/noalias.md) , [`noinline`](../cpp/noinline.md) , [`noreturn`](../cpp/noreturn.md) , [`nothrow`](../cpp/nothrow-cpp.md) , [`novtable`](../cpp/novtable.md) , [`process`](../cpp/process.md) , [`restrict`](../cpp/restrict.md) , [`safebuffers`](../cpp/safebuffers.md) ,, [`selectany`](../cpp/selectany.md) [`spectre`](../cpp/spectre.md) et [`thread`](../cpp/thread.md) . Il prend également en charge ces attributs d’objet COM : [`property`](../cpp/property-cpp.md) et [`uuid`](../cpp/uuid-cpp.md) .

Les attributs de classe de stockage,,,,,,,,, **`code_seg`** **`dllexport`** **`dllimport`** **`naked`** **`noalias`** **`nothrow`** **`property`** **`restrict`** **`selectany`** **`thread`** et **`uuid`** sont des propriétés uniquement de la déclaration de l’objet ou de la fonction à laquelle ils sont appliqués. L' **`thread`** attribut affecte uniquement les données et les objets. Les **`naked`** **`spectre`** attributs et affectent uniquement les fonctions. Les **`dllimport`** **`dllexport`** attributs et affectent les fonctions, les données et les objets. Les **`property`** **`selectany`** attributs, et **`uuid`** affectent les objets com.

Pour la compatibilité avec les versions précédentes, **`_declspec`** est un synonyme de, **`__declspec`** sauf si l’option de compilateur [/za \( Désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

Les **`__declspec`** Mots clés doivent être placés au début d’une déclaration simple. Le compilateur ignore, sans avertissement, les **`__declspec`** Mots clés placés après * ou & et devant l’identificateur de variable dans une déclaration.

Un **`__declspec`** attribut spécifié au début d’une déclaration de type défini par l’utilisateur s’applique à la variable de ce type. Par exemple :

```cpp
__declspec(dllimport) class X {} varX;
```

Dans ce cas, l'attribut s'applique à `varX`. Un **`__declspec`** attribut placé après le **`class`** **`struct`** mot clé ou s’applique au type défini par l’utilisateur. Par exemple :

```cpp
class __declspec(dllimport) X {};
```

Dans ce cas, l'attribut s'applique à `X`.

Les instructions générales pour l’utilisation **`__declspec`** de l’attribut pour les déclarations simples sont les suivantes :

*decl-specifier-SEQ* *init-declarator-List*;

*Decl-specifier-SEQ* doit contenir, entre autres choses, un type de base (par exemple,, **`int`** **`float`** un **`typedef`** ou un nom de classe), une classe de stockage (par exemple, **`static`** **`extern`** ) ou l' **`__declspec`** extension. La *liste init-declarator-List* doit contenir, entre autres choses, le pointeur partie des déclarations. Par exemple :

```cpp
__declspec(selectany) int * pi1 = 0;   //Recommended, selectany & int both part of decl-specifier
int __declspec(selectany) * pi2 = 0;   //OK, selectany & int both part of decl-specifier
int * __declspec(selectany) pi3 = 0;   //ERROR, selectany is not part of a declarator
```

Le code suivant déclare une variable locale de thread entière et lui affecte une valeur initiale :

```cpp
// Example of the __declspec keyword
__declspec( thread ) int tls_i = 1;
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Attributs du Storage-Class étendu C](../c-language/c-extended-storage-class-attributes.md)
