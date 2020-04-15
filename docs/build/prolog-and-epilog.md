---
title: Prologue et épilogue x64
ms.date: 12/17/2018
ms.assetid: 0453ed1a-3ff1-4bee-9cc2-d6d3d6384984
ms.openlocfilehash: d0b7444af6e434a09f6af5f5b1c144b46c79ad56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328433"
---
# <a name="x64-prolog-and-epilog"></a>Prologue et épilogue x64

Chaque fonction qui alloue de l’espace de pile, appelle d’autres fonctions, enregistre les registres non volontaires, ou utilise la manipulation d’exception doit avoir un prolog dont les limites d’adresse sont décrites dans les données de dénouement associées à l’entrée de table de fonction respective. Pour plus d’informations, voir [x64 traitement d’exception](../build/exception-handling-x64.md). Le prolog enregistre les registres d’argument dans leurs adresses à la maison si nécessaire, pousse des registres nonvolatiles sur la pile, alloue la partie fixe de la pile pour les habitants et les temporaires, et établit optionnellement un pointeur de cadre. Les données de dénouement associées doivent décrire l’action du prolog et doivent fournir les informations nécessaires pour annuler l’effet du code prolog.

Si l’allocation fixe dans la pile est de plus d’une page (c’est-à-dire supérieure à 4096 octets), alors il est possible que l’allocation de pile pourrait s’étendre sur plus d’une page de mémoire virtuelle et, par conséquent, l’allocation doit être vérifiée avant qu’elle ne soit allouée. Une routine spéciale qui est callable du prolog et qui ne détruit aucun des registres d’argument est prévu à cette fin.

La méthode préférée pour enregistrer les registres nonvolatiles est de les déplacer sur la pile avant l’allocation de pile fixe. Si l’allocation de pile fixe est effectuée avant que les registres nonvolatiles soient enregistrés, alors très probablement un déplacement de 32 bits est nécessaire pour traiter la zone de registre enregistrée. (Apparemment, les poussées des registres sont aussi rapides que les mouvements et devraient le rester dans un avenir prévisible en dépit de la dépendance implicite entre les poussées.) Les registres nonvolatiles peuvent être enregistrés dans n’importe quel ordre. Cependant, la première utilisation d’un registre non volatile dans le prolog doit être de le sauver.

## <a name="prolog-code"></a>Code Prolog

Le code d’un prolog typique peut être :

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    sub    RSP, fixed-allocation-size
    lea    R13, 128[RSP]
    ...
```

Ce prolog stocke l’argument registre RCX dans son emplacement à la maison, enregistre les registres nonvolatileS R13-R15, alloue la partie fixe du cadre de pile, et établit un pointeur de cadre qui pointe 128 octets dans la zone d’allocation fixe. L’utilisation d’un décalage permet de traiter une plus grande partie de la zone d’allocation fixe avec des compensations uniques.

Si la taille de l’allocation fixe est supérieure ou égale à une page de mémoire, alors une fonction d’aide doit être appelée avant de modifier le RER. Cette aide, `__chkstk`, sonde la gamme de piles à être alloué pour s’assurer que la pile est étendue correctement. Dans ce cas, l’exemple précédent de prolog serait plutôt :

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

L’aide `__chkstk` ne modifiera aucun registre autre que R10, R11, et les codes d’état. En particulier, il retournera RAX inchangé et laissera tous les registres non volontaires et les registres de passage d’arguments non modifiés.

## <a name="epilog-code"></a>Code Epilog

Le code Epilog existe à chaque sortie vers une fonction. Alors qu’il n’y a normalement qu’un seul prolog, il peut y avoir beaucoup d’épilogues. Le code Epilog réduit la pile à sa taille d’allocation fixe (si nécessaire), réploce l’allocation de pile fixe, restaure les registres non volatiles en faisant éclater leurs valeurs enregistrées de la pile, et renvoie.

Le code épilogue doit suivre un ensemble strict de règles pour que le code dénoué se déroule de façon fiable par des exceptions et des interruptions. Ces règles réduisent la quantité de données non ventilée requises, car aucune donnée supplémentaire n’est nécessaire pour décrire chaque épilogue. Au lieu de cela, le code de dénouement peut déterminer qu’une épilogue est exécutée en scannant vers l’avant à travers un flux de code pour identifier une épilogue.

Si aucun pointeur de cadre n’est employé dans la fonction, alors l’épilog doit d’abord traiter la partie fixe de la pile, les registres nonvolatiles sont sautés, et le contrôle est retourné à la fonction d’appel. Par exemple,

```MASM
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

Si un pointeur de cadre est utilisé dans la fonction, alors la pile doit être taillée à son allocation fixe avant l’exécution de l’épilog. Cette action ne fait techniquement pas partie de l’épilogue. Par exemple, l’épilog suivant pourrait être utilisé pour défaire le prolog précédemment utilisé :

```MASM
    lea      RSP, -128[R13]
    ; epilogue proper starts here
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

Dans la pratique, lorsqu’un pointeur de cadre est utilisé, il n’y a aucune bonne raison d’ajuster le RER en deux étapes, de sorte que l’épilogue suivant serait utilisé à la place :

```MASM
    lea      RSP, fixed-allocation-size - 128[R13]
    pop      R13
    pop      R14
    pop      R15
    ret
```

Ces formulaires sont les seuls légaux pour une épilogue. Il doit se `add RSP,constant` composer `lea RSP,constant[FPReg]`d’un ou , suivie d’une série de `return` zéro `jmp`ou plus 8-byte registre pops et a ou a . (Seul un sous-ensemble d’instructions `jmp` est permis dans l’épilogue. Le sous-ensemble est `jmp` exclusivement la classe des déclarations avec des références mémoire ModRM où mod mod valeur de champ ModRM est de 00. L’utilisation `jmp` d’instructions dans l’épilog avec ModRM mod valeur de champ 01 ou 10 est interdite. Voir le tableau A-15 dans le programmeur d’architecture AMD x86-64 Volume 3: General Purpose and System Instructions, pour plus d’informations sur les références ModRM autorisées.) Aucun autre code ne peut apparaître. En particulier, rien ne peut être programmé dans une épilogue, y compris le chargement d’une valeur de retour.

Lorsqu’un pointeur de cadre n’est pas utilisé, l’épilog doit utiliser `add RSP,constant` pour traiter la partie fixe de la pile. Il peut `lea RSP,constant[RSP]` ne pas utiliser à la place. Cette restriction existe de sorte que le code dénoué a moins de modèles à reconnaître lors de la recherche d’épilogues.

Le respect de ces règles permet au code de dénouer de déterminer qu’une épilogue est actuellement exécutée et de simuler l’exécution du reste de l’épilogue pour permettre de recréer le contexte de la fonction d’appel.

## <a name="see-also"></a>Voir aussi

[x64 Conventions logicielles](x64-software-conventions.md)
