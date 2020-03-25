---
title: __declspec
ms.date: 03/21/2019
f1_keywords:
- __declspec_cpp
- __declspec
- _declspec
helpviewer_keywords:
- __declspec keyword [C++]
ms.openlocfilehash: e0c99ea9379aa6e29096250e8bd36ce3d4f183e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180223"
---
# <a name="__declspec"></a>__declspec

**Section spécifique de Microsoft**

La syntaxe d’attribut étendu pour la spécification des informations de classe de stockage utilise le mot clé **__declspec** , qui spécifie qu’une instance d’un type donné doit être stockée avec un attribut de classe de stockage spécifique à Microsoft ci-dessous. Parmi les exemples d’autres modificateurs de classe de stockage figurent les mots clés **static** et **extern** . Toutefois, ces mots clés font partie de la spécification ANSI des langages C et C++ et, en tant que tels, ne sont pas couverts par la syntaxe à attributs étendus. La syntaxe à attributs étendus simplifie et normalise les extensions spécifiques à Microsoft pour les langages C et C++.

## <a name="grammar"></a>Grammaire

*decl-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec (** *Extended-decl-modifier-SEQ* **)**

*extended-decl-modifier-seq* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl-modifier* *Extended-decl-modifier-SEQ*

*extended-decl-modifier* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**aligner (** *#* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**allocate («** *segname* **»)**<br/>
&nbsp;&nbsp;&nbsp;**Allocator** de &nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**AppDomain**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg («** *segname* **»)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**déconseillé**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsic**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noalias**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noinline**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noreturn**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nothrow**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**novtable**<br/>
&nbsp;&nbsp;&nbsp;**processus** de &nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**propriété (** { **obtient =** _get_func_name_ &#124; **, put =** _put_func_name_ } **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**restreindre**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**spectre (nomitigation)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**thread**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**UUID («** *ComObjectGUID* **»)**

Un espace blanc sépare la séquence de modificateur de déclaration. Des exemples sont donnés dans des sections ultérieures.

La grammaire des attributs étendus prend en charge les attributs de classe de stockage spécifiques à Microsoft suivants : [align](../cpp/align-cpp.md), [allocation](../cpp/allocate.md), [allocator](../cpp/allocator.md), [AppDomain](../cpp/appdomain.md), [code_seg](../cpp/code-seg-declspec.md), [Deprecated](../cpp/deprecated-cpp.md), [dllexport](../cpp/dllexport-dllimport.md), [DllImport](../cpp/dllexport-dllimport.md), [jitintrinsic](../cpp/jitintrinsic.md), [Naked](../cpp/naked-cpp.md), [noalias](../cpp/noalias.md), [noinline](../cpp/noinline.md), [noreturn](../cpp/noreturn.md), [nothrow](../cpp/nothrow-cpp.md), [novtable](../cpp/novtable.md), [Process](../cpp/process.md), [restrict](../cpp/restrict.md), [safebuffers](../cpp/safebuffers.md), [selectany](../cpp/selectany.md), [ spectre](../cpp/spectre.md)et [thread](../cpp/thread.md). Il prend également en charge ces attributs d’objet COM : [Property](../cpp/property-cpp.md) et [UUID](../cpp/uuid-cpp.md).

Les attributs de classe de stockage **code_seg**, **dllexport**, **DllImport**, **Naked**, **noalias**, **nothrow**, **Property**, **restrict**, **selectany**, **thread**et **UUID** sont des propriétés uniquement de la déclaration de l’objet ou de la fonction à laquelle ils sont appliqués. L’attribut **thread** affecte uniquement les données et les objets. Les attributs **Naked** et **spectre** affectent uniquement les fonctions. Les attributs **DllImport** et **dllexport** affectent les fonctions, les données et les objets. Les attributs **Property**, **selectany**et **UUID** affectent les objets com.

Pour la compatibilité avec les versions précédentes, **_declspec** est un synonyme de **__declspec** sauf si l’option de compilateur [/za \(désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

Les mots clés **__declspec** doivent être placés au début d’une déclaration simple. Le compilateur ignore, sans avertissement, les mots clés **__declspec** placés après * ou & et devant l’identificateur de variable dans une déclaration.

Un attribut **__declspec** spécifié au début d’une déclaration de type défini par l’utilisateur s’applique à la variable de ce type. Par exemple :

```cpp
__declspec(dllimport) class X {} varX;
```

Dans ce cas, l'attribut s'applique à `varX`. Un **__declspec** attribut placé après le mot clé de **classe** ou de **struct** s’applique au type défini par l’utilisateur. Par exemple :

```cpp
class __declspec(dllimport) X {};
```

Dans ce cas, l'attribut s'applique à `X`.

La règle générale pour l’utilisation de l’attribut **__declspec** pour les déclarations simples est la suivante :

*decl-specifier-SEQ* *init-declarator-List*;

*Decl-specifier-SEQ* doit contenir, entre autres choses, un type de base (par exemple **, int**, **float**, un **typedef**ou un nom de classe), une classe de stockage (par exemple, **static**, **extern**) ou l’extension **__declspec** . La *liste init-declarator-List* doit contenir, entre autres choses, le pointeur partie des déclarations. Par exemple :

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

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[Attributs étendus de classe de stockage C](../c-language/c-extended-storage-class-attributes.md)
