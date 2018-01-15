---
title: bss_seg | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0dd1e24127129ef833cfd4906085eabbf1e5c380
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="bssseg"></a>bss_seg
Spécifie le segment où les variables non initialisées sont stockées dans le fichier .obj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma bss_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Notes  
 Fichiers obj peuvent être affichés avec le [dumpbin](../build/reference/dumpbin-command-line.md) application. Le segment par défaut dans le fichier .obj pour les données non initialisées est .bss. Dans certains cas l’utilisation de **bss_seg** peut accélérer les temps de chargement en regroupant les données non initialisées en une seule section.  
  
 **bss_seg** sans paramètre réinitialise le segment à .bss.  
  
 **push**(facultatif)  
 Place un enregistrement sur la pile interne du compilateur. A **push** peut avoir un *identificateur* et *segment-name*.  
  
 **POP** (facultatif)  
 Supprime un enregistrement du haut de la pile interne du compilateur.  
  
 *identificateur* (facultatif)  
 Lorsqu’il est utilisé avec **push**, attribue un nom à l’enregistrement sur la pile interne du compilateur. Lorsqu’il est utilisé avec **pop**, dépile les enregistrements de la pile interne jusqu'à ce que *identificateur* est supprimé ; si *identificateur* est introuvable sur la pile interne, rien n’est dépilé.  
  
 *identificateur* permet à plusieurs enregistrements d’être dépilés avec une seule **pop** commande.  
  
 *« nom du segment »*(facultatif)  
 Nom d'un segment. Lorsqu’il est utilisé avec **pop**, la pile est dépilée et *segment-name* devient le nom du segment actif.  
  
 *classe « segment »* (facultatif)  
 Incluse pour la compatibilité avec les versions de C++ antérieures à la version 2.0. Elle est ignorée.  
  
## <a name="example"></a>Exemple  
  
```  
// pragma_directive_bss_seg.cpp  
int i;                     // stored in .bss  
#pragma bss_seg(".my_data1")  
int j;                     // stored in "my_data1"  
  
#pragma bss_seg(push, stack1, ".my_data2")     
int l;                     // stored in "my_data2"  
  
#pragma bss_seg(pop, stack1)   // pop stack1 from stack  
int m;                     // stored in "stack_data1"  
  
int main() {  
}  
```  
  
 Vous pouvez également spécifier des sections pour les données initialisées ([data_seg](../preprocessor/data-seg.md)), fonctions ([code_seg](../preprocessor/code-seg.md)) et les variables const ([const_seg](../preprocessor/const-seg.md)).  
  
 Données allouées en utilisant le **bss_seg** pragma ne conserve aucune information concernant leur emplacement.  
  
 Consultez [/SECTION](../build/reference/section-specify-section-attributes.md) pour une liste de noms, vous ne devez pas utiliser lors de la création d’une section.  
  
## <a name="see-also"></a>Voir aussi  
 [Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)