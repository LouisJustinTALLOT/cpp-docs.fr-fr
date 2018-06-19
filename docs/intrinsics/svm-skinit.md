---
title: __svm_skinit | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_skinit
dev_langs:
- C++
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95e47608b7ec58e433d9be5e2f2178a825b6be2e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338102"
---
# <a name="svmskinit"></a>__svm_skinit
**Section spécifique à Microsoft**  
  
 Lance le chargement d’un logiciel sécurisé sécurisé, tel qu’un moniteur d’ordinateur virtuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __svm_skinit(  
   int SLB  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`SLB`|L’adresse physique de 32 bits d’un octet de 64 Ko Secure chargeur de bloc (SLB).|  
  
## <a name="remarks"></a>Notes  
 Le `__svm_skinit` fonction est équivalente à la `SKINIT` instruction machine. Cette fonction fait partie d’un système de sécurité qui utilise le processeur et un Module de plateforme approuvée (TPM) pour vérifier et charger des logiciels approuvés appelé un noyau de sécurité (SK). Un moniteur d’ordinateur virtuel est un exemple d’un noyau de sécurité. Le système de sécurité vérifie les composants du programme chargé pendant le processus d’initialisation et protège les composants contre la falsification à des interruptions, accès à l’appareil ou un autre programme si l’ordinateur est un multiprocesseur.  
  
 Le `SLB` paramètre spécifie l’adresse physique d’un bloc de 64 Ko de mémoire appelée le *sécuriser le bloc chargeur* (SLB). Le SLB contient un programme appelé le chargeur sécurisé qui établit l’environnement d’exploitation de l’ordinateur et par la suite charge le noyau de sécurité.  
  
 Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez le document, « de Volume manuelle AMD64 Architecture programmeur 2 : programmation du système, « numéro 24593, 3.11, de révision du document à la [corporation d’AMD](http://go.microsoft.com/fwlink/p/?linkid=23746) site.  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__svm_skinit`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)