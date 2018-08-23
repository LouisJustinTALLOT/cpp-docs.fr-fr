---
title: __svm_skinit | Microsoft Docs
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
ms.openlocfilehash: d0912b7a1ff41bf7a21da198268dbd4b8dc920a9
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42538681"
---
# <a name="svmskinit"></a>__svm_skinit
**Section spécifique à Microsoft**  
  
 Lance le chargement d’un logiciel sécurisé peut être vérifiée, par exemple un moniteur d’ordinateur virtuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __svm_skinit(  
   int SLB  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`SLB`|L’adresse physique de 32 bits d’un octet de 64 Ko du bloc de chargeur sécurisé (SLB).|  
  
## <a name="remarks"></a>Notes  
 Le `__svm_skinit` fonction est équivalente à la `SKINIT` instruction machine. Cette fonction fait partie d’un système de sécurité qui utilise le processeur et un Module de plateforme approuvés (TPM) pour vérifier et charger des logiciels approuvés appelé un noyau de sécurité (SK). Un moniteur d’ordinateur virtuel est un exemple d’un noyau de sécurité. Le système de sécurité vérifie les composants du programme chargés pendant le processus d’initialisation et protège les composants contre la falsification par des interruptions, accès des appareils ou un autre programme si l’ordinateur est un multiprocesseur.  
  
 Le `SLB` paramètre spécifie l’adresse physique d’un bloc de 64 Ko de la mémoire appelée le *bloc de chargeur sécurisé* (SLB). L’équilibreur SLB contient un programme appelé le chargeur sécurisé qui établit l’environnement d’exploitation de l’ordinateur et de charge par la suite le noyau de sécurité.  
  
 Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez dans le document, « manuelle Volume AMD64 Architecture pour le programmeur 2 : programmation du système, « 24593, révision 3.11, de numéro de document sur le [corporation d’AMD](http://go.microsoft.com/fwlink/p/?linkid=23746) site.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__svm_skinit`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)