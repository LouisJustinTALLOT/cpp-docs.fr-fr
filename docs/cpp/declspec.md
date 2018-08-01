---
title: __declspec | Microsoft Docs
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
ms.openlocfilehash: 4358712e5573095229a48a6d08b78706c608874d
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39403646"
---
# <a name="declspec"></a>__declspec

**Section spécifique à Microsoft**

La syntaxe à attributs étendus pour la spécification de classe de stockage d’informations utilise la **__declspec** mot clé, qui spécifie qu’une instance d’un type donné doit être stocké avec un attribut de classe de stockage spécifiques à Microsoft répertorié ci-dessous. Exemples d’autres modificateurs de classe de stockage la **statique** et **extern** mots clés. Toutefois, ces mots clés font partie de la spécification ANSI des langages C et C++ et, en tant que tels, ne sont pas couverts par la syntaxe à attributs étendus. La syntaxe à attributs étendus simplifie et normalise les extensions spécifiques à Microsoft pour les langages C et C++.

## <a name="grammar"></a>Grammaire

*decl-specifier*:  
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (**  *extended-decl-modifier-seq*  **)**

*extended-decl-modifier-seq* :  
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub>  
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl-modifier* *extended-decl-modifier-seq*

*extended-decl-modifier* :  
&nbsp;&nbsp;&nbsp;&nbsp;**Aligner (** *#* **)**  
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
&nbsp;&nbsp;&nbsp;&nbsp;**propriété (** { **obtenir =**_get_func_name_ &#124; **, put =**_put_func_name_ } **)**  
&nbsp;&nbsp;&nbsp;&nbsp;**restrict**  
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**  
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**  
&nbsp;&nbsp;&nbsp;&nbsp;**spectre(nomitigation)**  
&nbsp;&nbsp;&nbsp;&nbsp;**thread**  
&nbsp;&nbsp;&nbsp;&nbsp;**uuid("** *ComObjectGUID* **")**  

Un espace blanc sépare la séquence de modificateur de déclaration. Des exemples sont donnés dans des sections ultérieures.

Grammaire des attributs étendus prend en charge ces attributs de classe de stockage spécifique de Microsoft : [aligner](../cpp/align-cpp.md), [allouer](../cpp/allocate.md), [appdomain](../cpp/appdomain.md), [code_seg](../cpp/code-seg-declspec.md), [déconseillée](../cpp/deprecated-cpp.md), [dllexport](../cpp/dllexport-dllimport.md), [dllimport](../cpp/dllexport-dllimport.md), [jitintrinsic](../cpp/jitintrinsic.md), [naked](../cpp/naked-cpp.md), [noalias](../cpp/noalias.md), [noinline](../cpp/noinline.md), [noreturn](../cpp/noreturn.md), [nothrow](../cpp/nothrow-cpp.md), [novtable](../cpp/novtable.md) , [processus](../cpp/process.md), [restreindre](../cpp/restrict.md), [safebuffers](../cpp/safebuffers.md), [selectany](../cpp/selectany.md), [spectre](../cpp/spectre.md), et [thread](../cpp/thread.md). Il prend également en charge ces attributs d’objet COM : [propriété](../cpp/property-cpp.md) et [uuid](../cpp/uuid-cpp.md).

Le **code_seg**, **dllexport**, **dllimport**, **naked**, **noalias**, **nothrow** , **propriété**, **restreindre**, **selectany**, **thread**, et **uuid**les attributs de classe de stockage sont des propriétés uniquement de la déclaration de l’objet ou la fonction à laquelle ils s’appliquent. Le **thread** attribut affecte des données et uniquement les objets. Le **naked** et **spectre** attributs affectent uniquement les fonctions. Le **dllimport** et **dllexport** attributs affectent les fonctions, les données et les objets. Le **propriété**, **selectany**, et **uuid** attributs affectent les objets COM.

Le **__declspec** mots clés doivent être placés au début d’une déclaration simple. Le compilateur ignore sans avertissement les **__declspec** mots clés placés après * ou & et devant l’identificateur dans une déclaration de variable.

Un **__declspec** attribut spécifié au début d’une déclaration de type défini par l’utilisateur s’applique à la variable de ce type. Exemple :

```cpp
__declspec(dllimport) class X {} varX;
```

Dans ce cas, l'attribut s'applique à `varX`. Un **__declspec** attribut placé après le **classe** ou **struct** mot clé s’applique au type défini par l’utilisateur. Exemple :

```cpp
class __declspec(dllimport) X {};
```

Dans ce cas, l'attribut s'applique à `X`.

La règle générale pour l’utilisation de la **__declspec** attribut pour les déclarations simples est comme suit :

*decl-specifier-seq* *init-declarator-list*;

Le *decl-specifier-seq* doit contenir, entre autres choses, un type de base (par exemple, **int**, **float**, un **typedef**, ou un nom de classe), un classe de stockage (par exemple, **statique**, **extern**), ou le **__declspec** extension. Le *init-declarator-list* doit contenir, entre autres choses, la partie relative au pointeur des déclarations. Exemple :

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