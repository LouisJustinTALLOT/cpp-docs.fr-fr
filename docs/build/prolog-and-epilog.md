---
title: x64 prologue et épilogue
ms.date: 12/17/2018
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
ms.openlocfilehash: b808703e9c89b8e455e9df2b5959a2f0dd10b939
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627226"
---
# <a name="x64-prolog-and-epilog"></a>x64 prologue et épilogue

Chaque fonction qui alloue de l’espace de pile, appelle d’autres fonctions, enregistre les registres non volatils ou utilise la gestion des exceptions doit posséder un prologue dont les limites d’adresse sont décrites dans les données de déroulement associées à l’entrée de table de fonctions respective. Pour plus d’informations, consultez [x64 gestion des exceptions](../build/exception-handling-x64.md). Le prologue enregistre argument registres dans leurs adresses personnelles si nécessaire, pousse les registres non volatils sur la pile, alloue la partie fixe de la pile pour les variables locales et des objets temporaires et éventuellement établit un pointeur de frame. Données de déroulement associé doit décrire l’action du prologue et devez fournir les informations nécessaires pour annuler l’effet du code de prologue.

Si l’allocation fixe dans la pile est plus d’une page (autrement dit, supérieure à 4 096 octets), il est possible que l’allocation de pile peut s’étendre sur plusieurs pages de mémoire virtuelle et, par conséquent, l’allocation doit être vérifiée avant elle est allouée. Une routine spéciale qui peut être appelée depuis le prologue et qui ne détruit aucun des registres d’argument est fournie à cet effet.

La méthode recommandée pour l’enregistrement des registres non volatils consiste à les déplacer dans la pile avant l’allocation de pile fixe. Si l’allocation de pile fixe est effectuée avant que les registres non volatils sont enregistrés, puis très probablement un déplacement 32 bits est requis pour traiter la zone du Registre enregistré. (Plus ou moins, notifications push de registres sont aussi rapides que déplace et doit rester dans un avenir prévisible en dépit de la dépendance implicite entre les push.) Les registres non volatils peuvent être enregistrées dans n’importe quel ordre. Toutefois, la première utilisation d’un Registre non volatil dans le prologue doit être à l’enregistrer.

## <a name="prolog-code"></a>Code de prologue

Le code d’un prologue standard peut être :

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    sub    RSP, fixed-allocation-size
    lea    R13, 128[RSP]
    ...
```

Ce prologue stocke le Registre d’arguments RCX dans son emplacement d’origine, non volatile enregistre inscrit R13-R15, alloue la partie fixe du frame de pile et établit un pointeur de frame qui pointe de 128 octets dans la zone d’allocation fixe. À l’aide d’un offset permet plus de la zone d’allocation fixe à l’aide des décalages d’un octet.

Si la taille d’allocation fixe est supérieure ou égale à une page de mémoire, une fonction d’assistance doit être appelée avant de modifier RSP. Ce programme d’assistance, `__chkstk`, la plage de pile à allouer pour vous assurer que la pile est correctement étendue des sondes. Dans ce cas, l’exemple de prologue précédent serait à la place :

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    mov    RAX,  fixed-allocation-size
    call   __chkstk
    sub    RSP, RAX
    lea    R13, 128[RSP]
    ...
```

Le `__chkstk` helper ne modifiera pas des registres autres que R10, R11 et les codes de la condition. En particulier, il renverra RAX inchangé et laissez les registres de tous les non volatiles et les registres de transmission d’arguments tels quels.

## <a name="epilog-code"></a>Code d’épilogue

Le code d’épilogue se trouve à chaque sortie à une fonction. Alors qu’il est normalement qu’un seul prologue, il peut exister un grand nombre. Le code d’épilogue découpe la pile à sa taille d’allocation fixe (le cas échéant), libère la pile allocation fixe, restaure des registres non volatils en dépilant leurs valeurs enregistrées à partir de la pile et retourne.

Le code d’épilogue doit respecter un ensemble strict de règles pour le code de déroulement dérouler de manière fiable via les exceptions et d’interruptions. Ces règles de réduisent la quantité de données requises, de déroulement, car aucune donnée supplémentaire n’est nécessaire pour décrire chaque épilogue. Au lieu de cela, le code de déroulement peut déterminer qu’un épilogue est en cours d’exécution en analysant un flux de code pour identifier un épilogue.

Si aucun pointeur de frame n’est utilisé dans la fonction, l’épilogue doit d’abord libérer la partie fixe de la pile, les registres non volatils sont dépilés et contrôle est retourné à la fonction appelante. Par exemple :

```MASM
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

Si un pointeur de frame est utilisé dans la fonction, la pile doit être tronquée à son allocation fixe avant l’exécution de l’épilogue. Cette action est techniquement ne fait pas partie de l’épilogue. Par exemple, l’épilogue suivant peut servir à annuler le prologue utilisé précédemment :

```MASM
    lea      RSP, -128[R13]
    ; epilogue proper starts here
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

Dans la pratique, lorsqu’un pointeur de frame est utilisé, il n’existe aucune bonne raison d’ajuster RSP en deux étapes, de sorte que l’épilogue suivant serait utilisé à la place :

```MASM
    lea      RSP, fixed-allocation-size - 128[R13]
    pop      R13
    pop      R14
    pop      R15
    ret
```

Ces formulaires sont celles autorisées pour un épilogue. Il doit se composer d’un `add RSP,constant` ou `lea RSP,constant[FPReg]`, suivie d’une série de zéro ou plusieurs points de présence de registres de 8 octets et un `return` ou un `jmp`. (Seul un sous-ensemble de `jmp` instructions sont autorisées dans l’épilogue. Le sous-ensemble est exclusivement à la classe de `jmp` instructions avec les références de mémoires où la valeur du champ mod ModRM est 00. L’utilisation de `jmp` instructions dans l’épilogue avec ModRM mod champ valeur 01 ou 10 est interdite. Consultez A-15 Table AMD 64 x86 Architecture programmeur manuelle volume 3 : Usage général et les Instructions du système, pour plus d’informations sur les références ModRM autorisées.) Aucun autre code ne peut apparaître. En particulier, rien ne peut être planifié dans un épilogue, y compris le chargement d’une valeur de retour.

Lorsqu’un pointeur de frame n’est pas utilisé, l’épilogue doit utiliser `add RSP,constant` pour libérer la partie fixe de la pile. Il ne peut pas utiliser `lea RSP,constant[RSP]` à la place. Cette restriction existe par conséquent, le code de déroulement a moins de modèles pour reconnaître lors de la recherche d’épilogues.

Ces règles permet le code de déroulement pour déterminer qu’un épilogue est actuellement en cours d’exécution et de simuler l’exécution du reste de l’épilogue afin d’autoriser la recréation du contexte de la fonction appelante.

## <a name="see-also"></a>Voir aussi

[x64 conventions des logiciels](../build/x64-software-conventions.md)