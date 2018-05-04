---
title: struct UNWIND_CODE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 104955d8-7e33-4c5a-b0c6-3254648f0af3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 068acacf88e9ac968b34c26bf76657fd33adf4f3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="struct-unwindcode"></a>struct UNWIND_CODE
Le tableau des codes de déroulement est utilisé pour enregistrer la séquence d’opérations dans le prologue qui affectent les registres non volatils et RSP. Chaque élément de code a le format suivant :  
  
|||  
|-|-|  
|UBYTE|Offset dans le prologue|  
|UBYTE : 4|Code d’opération de déroulement|  
|UBYTE : 4|Information sur l’opération|  
  
 Le tableau est trié par ordre décroissant d’offset dans le prologue.  
  
 **Offset dans le prologue**  
 Décalage à partir du début du prologue de la fin de l’instruction qui effectue cette opération, plus 1 (autrement dit, le décalage du début de l’instruction suivante).  
  
 **Code d’opération de déroulement**  
 Remarque : Certains codes d’opération nécessite un offset non signé à une valeur dans le frame de pile local. Ce décalage est à partir du début (adresse la plus basse) de l’allocation de pile fixe. Si le champ du Registre du Frame dans UNWIND_INFO est zéro, ce décalage est from RSP. Si le champ du Registre du Frame est différent de zéro, il s’agit de l’offset où se situait RSP lorsque le registre FP a été établi. Cela équivaut au registre FP moins l’offset du Registre FP (16 * offset du Registre du frame mis à l’échelle dans UNWIND_INFO). Si un registre FP est utilisé, tout code de déroulement prenant un offset doit uniquement utilisée une fois le registre FP est établi dans le prologue.  
  
 Pour tous les codes d’opération à l’exception de UWOP_SAVE_XMM128 et UWOP_SAVE_XMM128_FAR, l’offset sera toujours un multiple de 8, car toutes les valeurs de la pile d’intérêt sont stockées sur les limites de 8 octets (la pile proprement dite est toujours alignée sur 16 octets). Pour les codes d’opération qui prennent un offset court (inférieur à 512 Ko), le dernier USHORT dans les nœuds pour ce code conserve l’offset divisé par 8. Pour les codes d’opération qui prennent un offset long (512 Ko < = décalage < 4 Go), les deux nœuds USHORT finals pour ce code maintenez le décalage (en format little-endian).  
  
 Pour les opcodes UWOP_SAVE_XMM128 et UWOP_SAVE_XMM128_FAR, l’offset sera toujours un multiple de 16, car toutes les opérations XMM de 128 bits doivent se produire sur 16 octets de mémoire alignée. Par conséquent, un facteur d’échelle de 16 est utilisé pour UWOP_SAVE_XMM128, autorisant ainsi les décalages de moins de 1 million.  
  
 Le code d’opération de déroulement est un des éléments suivants :  
  
 UWOP_PUSH_NONVOL (0) 1 nœud  
  
 Transmettre un registre entier non volatil, en décrémentant RSP de 8. Les informations de l’opération sont le numéro de l’historique. Notez que, en raison de contraintes sur les épilogues, les codes de déroulement UWOP_PUSH_NONVOL doivent s’affichent en premier dans le prologue et également en dernier dans le tableau des codes de déroulement. Ce classement relatif s’applique à tous les autres codes de déroulement à l’exception de UWOP_PUSH_MACHFRAME.  
  
 UWOP_ALLOC_LARGE (1) 2 ou 3 nœuds  
  
 Allouez une zone de grande taille sur la pile. Il existe deux formes. Si les informations de l’opération est égale à 0, alors que la taille de l’allocation divisée par 8 est enregistrée dans l’emplacement suivant, en autorisant une allocation jusqu'à 512 Ko - 8. Si les informations de l’opération est égal à 1, alors que la taille non ajustée de l’allocation est enregistrée dans les deux emplacements dans le format little-endian, ce qui permet les allocations jusqu'à 4 Go - 8.  
  
 UWOP_ALLOC_SMALL (2) 1 nœud  
  
 Allouez une zone de petite taille sur la pile. La taille de l’allocation est le champ d’information d’opération * 8 + 8, autorisant les allocations de 8 à 128 octets.  
  
 Le code de déroulement pour une pile d’allocation doit toujours utiliser l’encodage le plus court possible :  
  
|||  
|-|-|  
|**Taille d’allocation**|**Code de déroulement**|  
|8 à 128 octets|UWOP_ALLOC_SMALL|  
|136 à 512 Ko - 8 octets|UWOP_ALLOC_LARGE, information sur l’opération = 0|  
|512 Ko à 4 Go - 8 octets|UWOP_ALLOC_LARGE, information sur l’opération = 1|  
  
 UWOP_SET_FPREG (3) 1 nœud  
  
 Établir le Registre de pointeur de frame en définissant l’inscrire à un certain offset du RSP actuel. L’offset est égal au champ de l’offset du Registre du Frame (mis à l’échelle) dans UNWIND_INFO * 16, autorisant des offsets compris entre 0 et 240. L’utilisation d’un offset autorise l’établissement d’un pointeur de frame qui pointe vers le milieu de l’allocation de pile fixe, permettant ainsi de densité de code en permettant à plus d’accès à utiliser des formulaires d’instruction courts. Notez que le champ d’information d’opération est réservé et ne doit pas être utilisé.  
  
 UWOP_SAVE_NONVOL (4) 2 nœuds  
  
 Enregistrez un registre entier non volatil sur la pile à l’aide de MOV plutôt que de PUSH. Cela est principalement utilisé pour l’emballage, où un Registre non volatil est enregistré à la pile dans une position qui a été précédemment allouée. Les informations de l’opération sont le numéro de l’historique. L’offset de la pile de mise à l’échelle par 8 est enregistré dans la prochaine déroulement emplacement du code d’opération, comme décrit dans la Remarque ci-dessus.  
  
 UWOP_SAVE_NONVOL_FAR (5) 3 nœuds  
  
 Enregistrez un registre entier non volatil sur la pile avec un offset long, à l’aide de MOV plutôt que de PUSH. Cela est principalement utilisé pour l’emballage, où un Registre non volatil est enregistré à la pile dans une position qui a été précédemment allouée. Les informations de l’opération sont le numéro de l’historique. L’offset de pile non ajustée est enregistré dans la prochaine deux déroulement des emplacements de code d’opération, comme décrit dans la Remarque ci-dessus.  
  
 UWOP_SAVE_XMM128 (8) 2 nœuds  
  
 Enregistrez les 128 bits d’un registre XMM non volatil sur la pile. Les informations de l’opération sont le numéro de l’historique. L’offset de la pile de mise à l’échelle par 16 est enregistré à l’emplacement suivant.  
  
 UWOP_SAVE_XMM128_FAR (9) 3 nœuds  
  
 Enregistrez les 128 bits d’un registre XMM non volatil sur la pile avec un offset long. Les informations de l’opération sont le numéro de l’historique. L’offset de pile non ajustée est enregistrée dans les deux emplacements.  
  
 UWOP_PUSH_MACHFRAME (10) 1 nœud  
  
 Distribuer une image de l’ordinateur.  Cela est utilisé pour enregistrer l’effet d’une interruption matérielle ou une exception. Il existe deux formes. Si les informations de l’opération est égal à 0, les éléments suivants ont été envoyées sur la pile :  
  
|||  
|-|-|  
|RSP + 32|SS|  
|RSP + 24|Ancien RSP|  
|RSP + 16|EFLAGS|  
|RSP + 8|CS|  
|RSP|RIP|  
  
 Si les informations de l’opération est égale à 1, puis les éléments suivants ont à la place été envoyées :  
  
|||  
|-|-|  
|RSP + 40|SS|  
|RSP + 32|Ancien RSP|  
|RSP + 24|EFLAGS|  
|RSP + 16|CS|  
|RSP + 8|RIP|  
|RSP|Code d'erreur|  
  
 Ce code de déroulement s’affiche toujours dans un prologue factice, ce qui n’est jamais exécuté, mais au lieu de cela apparaît avant le point d’entrée réel d’une routine d’interruption et existe uniquement pour fournir un lieu pour simuler le push d’un frame de l’ordinateur. UWOP_PUSH_MACHFRAME enregistre cette simulation, ce qui indique l’ordinateur a sur le plan conceptuel effectué les étapes suivantes :  
  
 Affiche l’adresse de retour de RIP à partir du haut de la pile dans *Temp*  
  
 Push SS  
  
 Push ancien RSP  
  
 Push de EFLAGS  
  
 Push CS  
  
 Push *Temp*  
  
 Push de Code d’erreur (si les informations du maître d’opérations est égal à 1)  
  
 Le décrémente opération UWOP_PUSH_MACHFRAME de simulé RSP de 40 (information sur l’opération est égal à 0) ou 48 (information sur l’opération est égal à 1).  
  
 **Information sur l’opération**  
 La signification de ces 4 bits varie selon le code d’opération. Pour encoder un Registre à usage général (entier), le mappage suivant est utilisé :  
  
|||  
|-|-|  
|0|RAX|  
|1|RCX|  
|2|RDX|  
|3|RBX|  
|4|RSP|  
|5|RBP|  
|6|RSI|  
|7|RDI|  
|8 à 15|R8 à R15|  
  
## <a name="see-also"></a>Voir aussi  
 [Données de déroulement pour la gestion des exceptions et la prise en charge du débogueur](../build/unwind-data-for-exception-handling-debugger-support.md)