---
title: Prologue et épilogue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2939293fe5fbdfd07cb12470790de5b064489d7f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372007"
---
# <a name="prolog-and-epilog"></a>Prologue et épilogue
Chaque fonction qui alloue de l’espace de pile, appelle d’autres fonctions, enregistre les registres non volatils ou utilise la gestion des exceptions doit posséder un prologue dont les limites d’adresse sont décrites dans les données de déroulement associées à l’entrée de table de fonctions respective (consultez [(X64) de la gestion des exceptions](../build/exception-handling-x64.md)). Le prologue enregistre argument registres leurs adresses de base si nécessaire, exécute un push de registres non volatils sur la pile, alloue la partie fixe de la pile pour les variables locales et les objets temporaires et établit éventuellement un pointeur de frame. Données de déroulement associées doivent décrire l’action du prologue et devez fournir les informations nécessaires pour annuler l’effet du code de prologue.  
  
 Si l’allocation fixe dans la pile est plus d’une page (autrement dit, supérieure à 4 096 octets), il est possible que la pile d’allocation couvre plusieurs pages de mémoire virtuelle et, par conséquent, l’allocation doit être vérifiée avant qu’il est réellement allouée. Une routine spéciale qui peut être appelé par le prologue et qui ne détruit pas un des registres de l’argument est fournie à cet effet.  
  
 La méthode recommandée pour l’enregistrement des registres non volatils consiste à les déplacer dans la pile avant l’allocation de pile fixe. Si l’allocation de pile fixe a été effectuée avant que les registres non volatils ont été enregistrés, probablement un déplacement 32 bits est requis pour l’adresse de la zone de Registre enregistrée (plus ou moins, push de registres est aussi rapides que les déplacements et doit rester pour futur prévisible malgré la dépendance implicite entre les push). Les registres non volatils peuvent être enregistrés dans n’importe quel ordre. Toutefois, la première utilisation d’un Registre non volatil dans le prologue doit être à l’enregistrer.  
  
 Le code d’un prologue standard peut être :  
  
```  
mov       [RSP + 8], RCX  
push   R15  
push   R14  
push   R13  
sub      RSP, fixed-allocation-size  
lea      R13, 128[RSP]  
...  
```  
  
 Ce prologue stocke le Registre d’arguments RCX dans son emplacement d’origine, non volatile d’enregistre inscrit R13-R15, alloue la partie fixe du frame de pile et établit un pointeur de frame qui pointe de 128 octets dans la zone d’allocation fixe. À l’aide d’un offset permet plus de la zone d’allocation fixe à l’aide d’offsets d’un octet.  
  
 Si la taille d’allocation fixe est supérieure ou égale à une page de mémoire, une fonction d’assistance doit être appelée avant de modifier RSP. Ce programme d’assistance, __chkstk, est responsable de la détection de la plage à allouer la pile, pour vous assurer que la pile est correctement étendue. Dans ce cas, l’exemple de prologue précédent serait à la place :  
  
```  
mov       [RSP + 8], RCX  
push   R15  
push   R14  
push   R13  
mov      RAX,  fixed-allocation-size  
call   __chkstk  
sub      RSP, RAX  
lea      R13, 128[RSP]  
...  
```  
  
 L’application d’assistance __chkstk ne modifie aucun registre autre que R10, R11 et les codes de la condition. En particulier, elle retournera RAX inchangé et laisser tout non volatiles registres et les registres de transmission des arguments tels quels.  
  
 Le code d’épilogue se trouve à chaque sortie à une fonction. Alors qu’il est normalement qu’un seul prologue, il peut exister un grand nombre. Le code d’épilogue découpe la pile à sa taille d’allocation fixe (le cas échéant), libère la pile allocation fixe, restaure des registres non volatils en affichant leurs valeurs enregistrées à partir de la pile et retourne.  
  
 Le code d’épilogue doit respecter un ensemble strict de règles pour le code de déroulement dérouler de manière fiable via les exceptions et les interruptions. Cela réduit la quantité de données requises, de déroulement, car aucune donnée supplémentaire n’est nécessaire pour décrire chaque épilogue. Au lieu de cela, le code de déroulement peut déterminer qu’un épilogue est en cours d’exécution en analysant un flux de code pour identifier un épilogue.  
  
 Si aucun pointeur de frame n’est utilisé dans la fonction, l’épilogue doit d’abord libérer la partie fixe de la pile, les registres non volatils sont dépilés et contrôle soit retourné à la fonction appelante. Par exemple :  
  
```  
add      RSP, fixed-allocation-size  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 Si un pointeur de frame est utilisé dans la fonction, la pile doit être tronquée à son allocation fixe avant l’exécution de l’épilogue. Il s’agit techniquement ne fait pas partie de l’épilogue. Par exemple, l’épilogue suivant peut servir à annuler le prologue utilisé précédemment :  
  
```  
lea      RSP, -128[R13]  
; epilogue proper starts here  
add      RSP, fixed-allocation-size  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 Dans la pratique, lorsqu’un pointeur de frame est utilisé, il est inutile bon ajuster RSP en deux étapes, donc l’épilogue suivant serait utilisée à la place :  
  
```  
lea      RSP, fixed-allocation-size - 128[R13]  
pop      R13  
pop      R14  
pop      R15  
ret  
```  
  
 Ce sont les seules formes légales d’un épilogue. Il doit se composer d’un `add RSP,constant` ou `lea RSP,constant[FPReg]`, suivi d’une série de zéro ou plusieurs POP de registres de 8 octets et un retour ou une instruction jmp. (Seul un sous-ensemble d’instructions jmp sont autorisées dans l’épilogue. Elles sont exclusivement de la classe de jmps avec les références mémoires où la valeur de champ ModRM 00. L’utilisation d’instructions jmp dans l’épilogue avec la valeur de champ mod ModRM 01 ou 10 est interdite. A-15 voir une Table dans Manual Volume 3 le AMD 64 x86 Architecture programmeur : usage général et obtenir des Instructions du système, pour plus d’informations sur les références ModRM autorisées.). Aucun autre code ne peut apparaître. En particulier, rien ne peut être planifié dans un épilogue, y compris le chargement d’une valeur de retour.  
  
 Notez que, lorsqu’un pointeur de frame n’est pas utilisé, l’épilogue doit utiliser `add RSP,constant` pour libérer la partie fixe de la pile. Il ne peut pas utiliser `lea RSP,constant[RSP]` à la place. Cette restriction existe afin que le code de déroulement dispose de moins de modèles pour reconnaître lors de la recherche d’épilogues.  
  
 Ces règles permet le code de déroulement pour déterminer qu’un épilogue est actuellement en cours d’exécution et de simuler l’exécution du reste de l’épilogue afin d’autoriser la recréation du contexte de la fonction appelante.  
  
## <a name="see-also"></a>Voir aussi  
 [Conventions des logiciels x64](../build/x64-software-conventions.md)