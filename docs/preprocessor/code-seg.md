---
title: code_seg | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- code_seg_CPP
- vc-pragma.code_seg
dev_langs:
- C++
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f958d1652f82f297ae530c1e24bdf331976e0dc0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839071"
---
# <a name="codeseg"></a>code_seg
Spécifie le segment de texte dans lequel les fonctions sont stockées dans un fichier .obj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma code_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Notes  
 La directive de pragma `code_seg` ne contrôle pas l'emplacement de code objet généré pour les modèles instanciés, ni le code généré de manière implicite par le compilateur (par exemple, les fonctions membres spéciales). Nous vous recommandons d’utiliser le [__declspec(code_seg(...)) ](../cpp/code-seg-declspec.md) d’attribut à la place, car elle vous donne contrôler l’emplacement de tout le code objet. Cela comprend le code généré par le compilateur.  
  
 A *segment* dans un .obj fichier est un bloc nommé de données qui sont chargés en mémoire en tant qu’unité. A *segment de texte* est un segment qui contienne du code exécutable. Dans cet article, les termes du contrat *segment* et *section* sont utilisés indifféremment.  
  
 La directive de pragma `code_seg` indique au compilateur de déplacer tout prochain code objet de l'unité de traduction vers un segment de texte nommé `segment-name`. Par défaut, le segment de texte utilisé pour les fonctions d'un fichier .obj est nommé ".text".  
  
 Une directive de pragma `code_seg` sans paramètres réinitialise le nom du segment de texte en ".text" pour le prochain code objet.  
  
 **Push** (facultatif)  
 Place un enregistrement sur la pile interne du compilateur. A **push** peut avoir un `identifier` et `segment-name`.  
  
 **POP** (facultatif)  
 Supprime un enregistrement du haut de la pile interne du compilateur.  
  
 `identifier`(facultatif)  
 Lorsqu’il est utilisé avec **push**, attribue un nom à l’enregistrement sur la pile interne du compilateur. Lorsqu’il est utilisé avec **pop**, dépile les enregistrements de la pile interne jusqu'à ce que `identifier` est supprimé ; si `identifier` est introuvable sur la pile interne, rien n’est dépilé.  
  
 `identifier` permet à plusieurs enregistrements d’être dépilés avec un seul **pop** commande.  
  
 "`segment-name`" (facultatif)  
 Nom d'un segment. Lorsqu’il est utilisé avec **pop**, la pile est dépilée et `segment-name` devient le nom de segment de texte actif.  
  
 "`segment-class`" (facultatif)  
 Ignoré, mais inclus pour des raisons de compatibilité avec les versions de C++ antérieures à la version 2.0.  
  
 Vous pouvez utiliser la [DUMPBIN. EXE](../build/reference/dumpbin-command-line.md) application pour afficher les fichiers .obj. [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] comprend une version de DUMPBIN pour chaque architecture cible prise en charge.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment utiliser la directive de pragma `code_seg` afin de contrôler l'emplacement du code objet :  
  
```  
// pragma_directive_code_seg.cpp  
void func1() {                  // stored in .text  
}  
  
#pragma code_seg(".my_data1")  
void func2() {                  // stored in my_data1  
}  
  
#pragma code_seg(push, r1, ".my_data2")  
void func3() {                  // stored in my_data2  
}  
  
#pragma code_seg(pop, r1)      // stored in my_data1  
void func4() {  
}  
  
int main() {  
}  
```  
  
 Pour obtenir la liste des noms qui ne doit pas être utilisé pour créer une section, consultez [/SECTION](../build/reference/section-specify-section-attributes.md).  
  
 Vous pouvez également spécifier des sections pour les données initialisées ([data_seg](../preprocessor/data-seg.md)), données non initialisées ([bss_seg](../preprocessor/bss-seg.md)) et les variables const ([const_seg](../preprocessor/const-seg.md)).  
  
## <a name="see-also"></a>Voir aussi  
 [code_seg (__declspec)](../cpp/code-seg-declspec.md)   
 [Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)