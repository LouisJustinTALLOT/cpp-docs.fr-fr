---
title: '#Directives ifdef et #ifndef (C/C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#ifndef'
- '#ifdef'
dev_langs:
- C++
helpviewer_keywords:
- '#ifdef directive'
- preprocessor, directives
- ifdef directive (#ifdef)
- ifndef directive (#ifndef)
- '#ifndef directive'
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c3453cd652401e9d1f4573bb1750773cbefe8d9
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2018
ms.locfileid: "42538634"
---
# <a name="ifdef-and-ifndef-directives-cc"></a>Directives #ifdef et #ifndef (C/C++)
Le **#ifdef** et **#ifndef** directives effectuant la même tâche que le `#if` directive lorsqu’il est utilisé avec **défini**( *identificateur* ).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#ifdef identifier  
#ifndef identifier  
  
// equivalent to  
#if defined identifier  
#if !defined identifier  
```  
  
## <a name="remarks"></a>Notes  
 
Vous pouvez utiliser la **#ifdef** et **#ifndef** directives n’importe où `#if` peut être utilisé. Le **#ifdef** *identificateur* instruction est équivalente à `#if 1` lorsque *identificateur* a été défini, et il est équivalent à `#if 0` lorsque *identificateur* n’a pas été défini ou a été supprimée avec la `#undef` directive. Ces directives vérifient uniquement la présence ou l'absence d'identificateurs définis avec `#define`, et non d'identificateurs déclarés dans le code source C ou C++.  
  
Ces directives sont fournies uniquement pour des raisons de compatibilité avec les versions antérieures du langage. Le **défini (** *identificateur* **)** expression constante utilisée avec la `#if` directive est préférée.  
  
Le **#ifndef** directive vérifie l’inverse de la condition vérifiée par **#ifdef**. Si l'identificateur n'a pas été défini (ou si sa définition a été supprimée avec `#undef`), la condition est vraie (non nulle). Sinon, la condition n'est pas vérifiée (0).  
  
**Section spécifique à Microsoft**  
  
Le *identificateur* peuvent être passés à partir de la ligne de commande à l’aide de la `/D` option. Jusqu'à 30 macros peut être spécifiée avec `/D`.  
  
Cela est utile pour vérifier si une définition existe, car une définition peut être transmise à partir de la ligne de commande. Exemple :  
  
```cpp  
// ifdef_ifndef.CPP  
// compile with: /Dtest /c  
#ifndef test  
#define final  
#endif  
```  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 
[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)