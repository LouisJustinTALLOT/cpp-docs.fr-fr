---
title: __declspec | Documents Microsoft
ms.custom: ''
ms.date: 1/23/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __declspec_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++]
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c610da3545e7269c307542930140616dc6af9dce
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418287"
---
# <a name="declspec"></a>__declspec

**Section spécifique à Microsoft**

La syntaxe à attributs étendus pour la spécification de classe de stockage d’informations utilise le **__declspec** mot clé, qui spécifie qu’une instance d’un type donné doit être stocké avec un attribut de classe de stockage spécifique à Microsoft ci-dessous. Exemples d’autres modificateurs de classe de stockage incluent les **statique** et **extern** mots clés. Toutefois, ces mots clés font partie de la spécification ANSI des langages C et C++ et, en tant que tels, ne sont pas couverts par la syntaxe à attributs étendus. La syntaxe à attributs étendus simplifie et normalise les extensions spécifiques à Microsoft pour les langages C et C++.

## <a name="grammar"></a>Grammaire

*spécificateur de déclaration*:  
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (**  *extended-decl-modifier-seq*  **)**

*extended-decl-modifier-seq* :  
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub>  
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl-modifier* *extended-decl-modifier-seq*

*extended-decl-modifier* :  
&nbsp;&nbsp;&nbsp;&nbsp;**align (** *#* **)**  
&nbsp;&nbsp;&nbsp;&nbsp;**allocate("** *segname* **")**  
&nbsp;&nbsp;&nbsp;&nbsp;**appdomain**  
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg("** *segname* **")**  
&nbsp;&nbsp;&nbsp;&nbsp;**Déconseillé**  
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**  
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**  
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsic**  
&nbsp;&nbsp;&nbsp;&nbsp;**naked**  
&nbsp;&nbsp;&nbsp;&nbsp;**noalias**  
&nbsp;&nbsp;&nbsp;&nbsp;**noinline**  
&nbsp;&nbsp;&nbsp;&nbsp;**noreturn**  
&nbsp;&nbsp;&nbsp;&nbsp;**nothrow**  
&nbsp;&nbsp;&nbsp;&nbsp;**novtable**  
&nbsp;&nbsp;&nbsp;&nbsp;**Processus**  
&nbsp;&nbsp;&nbsp;&nbsp;**propriété (** { **get =**_get_func_name_ &#124; **, put =**_put_func_name_ } **)**  
&nbsp;&nbsp;&nbsp;&nbsp;**restrict**  
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**  
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**  
&nbsp;&nbsp;&nbsp;&nbsp;**spectre(nomitigation)**  
&nbsp;&nbsp;&nbsp;&nbsp;**thread**  
&nbsp;&nbsp;&nbsp;&nbsp;**uuid("** *ComObjectGUID* **")**  

Un espace blanc sépare la séquence de modificateur de déclaration. Des exemples sont donnés dans des sections ultérieures.

Ces attributs de classe de stockage spécifique à Microsoft prend en charge la grammaire de l’attribut étendu : [aligner](../cpp/align-cpp.md), [allouer](../cpp/allocate.md), [appdomain](../cpp/appdomain.md), [code_seg](../cpp/code-seg-declspec.md), [déconseillée](../cpp/deprecated-cpp.md), [dllexport](../cpp/dllexport-dllimport.md), [dllimport](../cpp/dllexport-dllimport.md), [jitintrinsic](../cpp/jitintrinsic.md), [naked](../cpp/naked-cpp.md), [noalias](../cpp/noalias.md), [noinline](../cpp/noinline.md), [noreturn](../cpp/noreturn.md), [nothrow](../cpp/nothrow-cpp.md), [novtable](../cpp/novtable.md) , [processus](../cpp/process.md), [restreindre](../cpp/restrict.md), [safebuffers](../cpp/safebuffers.md), [selectany](../cpp/selectany.md), [spectre](../cpp/spectre.md), et [thread](../cpp/thread.md). Il prend également en charge ces attributs d’objet COM : [propriété](../cpp/property-cpp.md) et [uuid](../cpp/uuid-cpp.md).

Le **code_seg**, **dllexport**, **dllimport**, **naked**, **noalias**, **nothrow** , **propriété**, **restreindre**, **selectany**, **thread**, et **uuid**les attributs de classe de stockage sont des propriétés uniquement de la déclaration de l’objet ou la fonction à laquelle elles sont appliquées. Le **thread** attribut affecte les données et les objets uniquement. Le **naked** et **spectre** attributs affectent uniquement les fonctions. Le **dllimport** et **dllexport** attributs affectent les fonctions, les données et les objets. Le **propriété**, **selectany**, et **uuid** attributs affectent les objets COM.

Le **__declspec** mots clés doivent être placés au début d’une déclaration simple. Le compilateur ignore sans avertissement les **__declspec** mots clés placés après * ou & et devant l’identificateur dans une déclaration de variable.

A **__declspec** attribut spécifié au début d’une déclaration de type défini par l’utilisateur s’applique à la variable de ce type. Par exemple :

```cpp
__declspec(dllimport) class X {} varX;
```

Dans ce cas, l'attribut s'applique à `varX`. A **__declspec** attribut placé après le **classe** ou **struct** mot clé s’applique au type défini par l’utilisateur. Par exemple :

```cpp
class __declspec(dllimport) X {};
```

Dans ce cas, l'attribut s'applique à `X`.

La règle générale pour l’utilisation de la **__declspec** attribut pour les déclarations simples est la suivante :

*decl-specifier-seq* *init-declarator-list*;

Le *decl-specifier-seq* doit contenir, entre autres choses, un type de base (par exemple, **int**, **float**, un **typedef**, ou un nom de classe), un classe de stockage (par exemple, **statique**, **extern**), ou le **__declspec** extension. Le *init-declarator-list* doit contenir, entre autres choses, le pointeur de déclarations. Par exemple :

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

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)  
[Attributs étendus de classe de stockage C](../c-language/c-extended-storage-class-attributes.md)  
