---
title: ATL (inscription) et les arborescences d’analyse | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bb5b132e5e55ab5336254acaf4d2d3ae25440697
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358827"
---
# <a name="understanding-parse-trees"></a>Présentation des arborescences d’analyse
Vous pouvez définir une ou plusieurs arborescences d’analyse dans votre script registrar où chaque arborescence d’analyse a la forme suivante :  
  
```  
<root key>{<registry expression>}+  
```  
  
 où :  
  
```  
<root key> ::= HKEY_CLASSES_ROOT | HKEY_CURRENT_USER |  
    HKEY_LOCAL_MACHINE | HKEY_USERS |  
    HKEY_PERFORMANCE_DATA | HKEY_DYN_DATA |  
    HKEY_CURRENT_CONFIG | HKCR | HKCU |  
    HKLM | HKU | HKPD | HKDD | HKCC  
<registry expression> ::= <Add Key> | <Delete Key>  
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>  
 [<Key Value>][{<Add Key>}]  
<Delete Key> ::= Delete<Key Name>  
<Key Name> ::= '<AlphaNumeric>+'  
<AlphaNumeric> ::= any character not NULL, i.e. ASCII 0  
<Key Value> ::== <Key Type><Key Name>  
<Key Type> ::= s | d  
<Key Value> ::= '<AlphaNumeric>'  
```  
  
> [!NOTE]
> `HKEY_CLASSES_ROOT` et `HKCR` sont équivalentes ; `HKEY_CURRENT_USER` et `HKCU` sont équivalents ; et ainsi de suite.  
  
 Une arborescence d’analyse peut ajouter plusieurs clés et des sous-clés pour la \<clé racine >. Ce faisant, il conserve un handle de sous-clé ouvert jusqu'à ce que l’analyseur a terminé l’analyse de toutes ses sous-clés. Cette approche est plus efficace que le traitement d’une clé unique à la fois, comme illustré dans l’exemple suivant :  
  
```  
HKEY_CLASSES_ROOT  
{  
 'MyVeryOwnKey'  
 {  
 'HasASubKey'  
 {  
 'PrettyCool'  
 }  
 }  
}  
```  
  
 Ici, le bureau d’enregistrement s’affiche initialement (crée) `HKEY_CLASSES_ROOT\MyVeryOwnKey`. Elle constate que `MyVeryOwnKey` a une sous-clé. Plutôt que la fermeture de la clé à `MyVeryOwnKey`, le bureau d’enregistrement conserve le handle et ouvre (crée) `HasASubKey` à l’aide de ce handle parent. (Le Registre système peut être plus lent quand aucun handle parent n’est ouvert.) Par conséquent, ouverture `HKEY_CLASSES_ROOT\MyVeryOwnKey` , puis en ouvrant `HasASubKey` avec `MyVeryOwnKey` comme parent est plus rapide que lors de l’ouverture `MyVeryOwnKey`, fermeture `MyVeryOwnKey`, puis en ouvrant `MyVeryOwnKey\HasASubKey`.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de scripts d’inscription](../atl/creating-registrar-scripts.md)

