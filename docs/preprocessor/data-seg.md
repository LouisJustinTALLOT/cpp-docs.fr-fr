---
title: data_seg | Microsoft Docs
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
ms.openlocfilehash: 9841b74d7bef74a117350b84747a606043d05d67
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707666"
---
# <a name="dataseg"></a>data_seg
Spécifie le segment de données où les variables initialisées sont stockées dans le fichier .obj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma data_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
### <a name="parameters"></a>Paramètres

**push**<br/>
(Facultatif) Place un enregistrement sur la pile interne du compilateur. Un **push** peut avoir un *identificateur* et *segment-name*.  

**pop**<br/>
(Facultatif) Supprime un enregistrement à partir du haut de la pile interne du compilateur.  
  
*identifier*<br/>
(Facultatif) Lorsqu’il est utilisé avec **push**, assigne un nom à l’enregistrement sur la pile interne du compilateur. Lorsqu’il est utilisé avec **pop**, dépile les enregistrements de la pile interne jusqu'à ce que *identificateur* est supprimé ; si *identificateur* est introuvable sur la pile interne, rien n’est dépilé.  
  
*identificateur* permet à plusieurs enregistrements à dépiler avec une seule **pop** commande.  
  
*« segment-name »*<br/>
(Facultatif) Le nom d’un segment. Lorsqu’il est utilisé avec **pop**, la pile est dépilée et *segment-name* devient le nom de segment actif.  
  
*« segment-class »*<br/>
(Facultatif) Inclus pour la compatibilité avec C++ antérieures à la version 2.0. Elle est ignorée.  
  
## <a name="remarks"></a>Notes 

La signification des termes du contrat *segment* et *section* sont interchangeables dans cette rubrique.  
  
Les fichiers OBJ peuvent être affichés avec le [dumpbin](../build/reference/dumpbin-command-line.md) application. Le segment par défaut dans le fichier .obj pour les variables initialisées est .data. Les variables qui ne sont pas initialisées doivent être initialisées sur zéro et sont stockées dans .bss.  
  
**data_seg** sans paramètres réinitialise le segment sur .data.

## <a name="example"></a>Exemple  
  
```cpp  
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
  
Consultez [/SECTION](../build/reference/section-specify-section-attributes.md) pour obtenir la liste des noms que vous ne devez pas utiliser lors de la création d’une section.  
  
Vous pouvez également spécifier des sections pour les variables const ([const_seg](../preprocessor/const-seg.md)), données non initialisées ([bss_seg](../preprocessor/bss-seg.md)) et les fonctions ([code_seg](../preprocessor/code-seg.md)).  
  
## <a name="see-also"></a>Voir aussi  
 
[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)