---
title: __fastfail | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 9cd32639-e395-4c75-9f3a-ac3ba7f49921
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f7a9fe4f4a70f55061addab05f90bda389fd8949
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="fastfail"></a>__fastfail
**Section spécifique à Microsoft**  
  
 Arrête immédiatement le processus appelant avec une surcharge minimale.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __fastfail(unsigned int code);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `code`  
 Constante symbolique `FAST_FAIL_<description>` de winnt.h ou wdm.h qui indique la raison de l'arrêt du processus.  
  
## <a name="return-value"></a>Valeur de retour  
 Le `__fastfail` intrinsèque ne retourne pas.  
  
## <a name="remarks"></a>Remarques  
 Le `__fastfail` intrinsèque fournit un mécanisme pour un *rapide échouent* demande : un moyen pour un processus potentiellement endommagé à l’arrêt immédiat du processus de demande. Les défaillances critiques qui ont peut-être endommagé l'état du programme et la pile au-delà de toute récupération ne peuvent pas être gérées par la fonctionnalité de gestion des exceptions ordinaire. Utilisez `__fastfail` pour arrêter le processus à l'aide d'une surcharge minimale.  
  
 En interne, `__fastfail` est implémentée à l'aide de plusieurs mécanismes spécifiques à l'architecture :  
  
|Architecture|Instruction|Emplacement de l'argument de code|  
|------------------|-----------------|-------------------------------|  
|x86|int 0x29|ecx|  
|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|int 0x29|rcx|  
|ARM|Opcode 0xDEFB|r0|  
  
 Une demande de basculement rapide est autonome et son exécution ne nécessite généralement que deux instructions. Une fois qu'une demande de basculement rapide a été exécutée, le noyau exécute l'action appropriée. Dans le code en mode utilisateur, il n'existe aucune dépendance de mémoire au-delà du pointeur d'instruction proprement dit quand un événement de basculement rapide est déclenché. Cela permet d'optimiser la fiabilité même en cas de grave endommagement de la mémoire.  
  
 L'argument `code` (l'une des constantes symboliques `FAST_FAIL_<description>` de winnt.h ou wdm.h) décrit le type de condition d'échec. Il est intégré aux rapports d'échec d'une manière spécifique à l'environnement.  
  
 Les demandes de basculement rapide en mode utilisateur apparaissent comme une exception non continuelle de deuxième chance avec le code d'exception 0xC0000409 et avec au moins un paramètre d'exception. Le premier paramètre de l'exception est la valeur `code`. Ce code d'exception indique à l'infrastructure de débogage et de Rapport d'erreurs Windows que le processus est endommagé et que des actions in-process minimales doivent être effectuées en réponse à l'échec. Les demandes de basculement rapide en mode noyau sont implémentées à l'aide d'un code de vérification d'erreur dédié, `KERNEL_SECURITY_CHECK_FAILURE` (0x139). Dans les deux cas, aucun gestionnaire d'exceptions n'est appelé car le programme est censé être dans un état endommagé. Si un débogueur est présent, il a la possibilité d'examiner l'état du programme avant son arrêt.  
  
 La prise en charge du mécanisme de basculement rapide natif est apparue dans Windows 8. Les systèmes d'exploitation Windows qui ne prennent pas en charge l'instruction de basculement rapide en mode natif traitent généralement une demande de basculement rapide comme une violation d'accès ou comme une vérification d'erreur `UNEXPECTED_KERNEL_MODE_TRAP`. Dans ces cas-là, le programme est tout de même arrêté, mais pas nécessairement au rapidement.  
  
 `__fastfail` est uniquement disponible en tant qu'intrinsèque.  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__fastfail`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)], ARM|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)