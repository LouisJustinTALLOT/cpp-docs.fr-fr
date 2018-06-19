---
title: data_seg | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- data_seg_CPP
- vc-pragma.data_seg
dev_langs:
- C++
helpviewer_keywords:
- data_seg pragma
- pragmas, data_seg
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a463d966c681557525bb9512762731c01a7ce30
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33841230"
---
# <a name="dataseg"></a>data_seg
Spécifie le segment de données où les variables initialisées sont stockées dans le fichier .obj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
#pragma data_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Notes  
 La signification des termes du contrat *segment* et *section* sont interchangeables dans cette rubrique.  
  
 Fichiers OBJ peuvent être affichés avec le [dumpbin](../build/reference/dumpbin-command-line.md) application. Le segment par défaut dans le fichier .obj pour les variables initialisées est .data. Les variables qui ne sont pas initialisées doivent être initialisées sur zéro et sont stockées dans .bss.  
  
 **data_seg** sans paramètre réinitialise le segment sur .data.  
  
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
// pragma_directive_data_seg.cpp  
int h = 1;                     // stored in .data  
int i = 0;                     // stored in .bss  
#pragma data_seg(".my_data1")  
int j = 1;                     // stored in "my_data1"  
  
#pragma data_seg(push, stack1, ".my_data2")     
int l = 2;                     // stored in "my_data2"  
  
#pragma data_seg(pop, stack1)   // pop stack1 off the stack  
int m = 3;                     // stored in "stack_data1"  
  
int main() {  
}  
```  
  
 Données allouées en utilisant **data_seg** ne conserve pas toutes les informations concernant son emplacement.  
  
 Consultez [/SECTION](../build/reference/section-specify-section-attributes.md) pour une liste de noms, vous ne devez pas utiliser lors de la création d’une section.  
  
 Vous pouvez également spécifier des sections pour les variables const ([const_seg](../preprocessor/const-seg.md)), données non initialisées ([bss_seg](../preprocessor/bss-seg.md)) et les fonctions ([code_seg](../preprocessor/code-seg.md)).  
  
## <a name="see-also"></a>Voir aussi  
 [Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)