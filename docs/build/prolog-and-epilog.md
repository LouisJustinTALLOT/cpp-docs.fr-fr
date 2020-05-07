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

Chaque fonction qui alloue de l’espace de pile, appelle d’autres fonctions, enregistre les registres non volatiles, ou utilise la gestion des exceptions doit avoir un prologue dont les limites d’adresse sont décrites dans les données de déroulement associées à l’entrée de table de fonctions respective. Pour plus d’informations, consultez [gestion des exceptions x64](../build/exception-handling-x64.md). Le prologue enregistre les registres d’arguments dans leurs adresses personnelles, si nécessaire, exécute un push des registres non volatils sur la pile, alloue la partie fixe de la pile pour les variables locales et les paramètres de temporisation, et établit éventuellement un pointeur de frame. Les données de déroulement associées doivent décrire l’action du prologue et fournir les informations nécessaires pour annuler l’effet du code de prologue.

Si l’allocation fixe dans la pile est plus d’une page (autrement dit, plus de 4096 octets), il est possible que l’allocation de pile puisse s’étendre sur plusieurs pages de mémoire virtuelle et, par conséquent, l’allocation doit être vérifiée avant d’être allouée. Une routine spéciale qui peut être appelée à partir du prologue et qui ne détruit aucun des registres des arguments est fournie à cet effet.

La méthode recommandée pour enregistrer des registres non volatils consiste à les déplacer sur la pile avant l’allocation de pile fixe. Si l’allocation de pile fixe est effectuée avant l’enregistrement des registres non volatils, il est probable qu’un déplacement de 32 bits soit requis pour adresser la zone de Registre enregistrée. (Signalées, les notifications push des registres sont aussi rapides que les déplacements et devraient rester pour l’avenir prévisible en dépit de la dépendance implicite entre les push.) Les registres non volatiles peuvent être enregistrés dans n’importe quel ordre. Toutefois, la première utilisation d’un registre non volatil dans le prologue doit être l’enregistrement.

## <a name="prolog-code"></a>Code de prologue

Le code d’un prologue classique peut être :

```MASM
    mov    [RSP + 8], RCX
    push   R15
    push   R14
    push   R13
    sub    RSP, fixed-allocation-size
    lea    R13, 128[RSP]
    ...
```

Ce prologue stocke l’argument Register RCX à son emplacement d’hébergement, enregistre les registres non volatils R13-R15, alloue la partie fixe du frame de pile et établit un pointeur de frame qui pointe 128 octets dans la zone d’allocation fixe. L’utilisation d’un décalage permet de traiter une plus grande partie de la zone d’allocation fixe avec des décalages d’un octet.

Si la taille d’allocation fixe est supérieure ou égale à une page de mémoire, une fonction d’assistance doit être appelée avant la modification de RSP. Cette application d’assistance `__chkstk`,, sonde la plage de la pile à allouer pour s’assurer que la pile est correctement étendue. Dans ce cas, l’exemple de prologue précédent serait à la place :

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

L' `__chkstk` application auxiliaire ne modifiera pas les registres autres que R10, R11 et les codes de condition. En particulier, elle retourne RAX inchangé et laisse tous les registres non volatiles et les registres de passage d’argument non modifiés.

## <a name="epilog-code"></a>Code d’épilogue

Le code d’épilogue existe à chaque sortie d’une fonction. Alors qu’il n’y a généralement qu’un seul prologue, il peut y avoir plusieurs épilogues. Le code d’épilogue tronque la pile à sa taille d’allocation fixe (si nécessaire), libère l’allocation de pile fixe, restaure les registres non volatils en dépilant leurs valeurs enregistrées de la pile et retourne.

Le code d’épilogue doit suivre un ensemble strict de règles pour le code de déroulement afin de dérouler de manière fiable les exceptions et les interruptions. Ces règles réduisent la quantité de données de déroulement requises, car aucune donnée supplémentaire n’est nécessaire pour décrire chaque épilogue. Au lieu de cela, le code de déroulement peut déterminer qu’un épilogue est en cours d’exécution en analysant par progression un flux de code pour identifier un épilogue.

Si aucun pointeur de frame n’est utilisé dans la fonction, l’épilogue doit d’abord libérer la partie fixe de la pile, les registres non volatils sont dépilés et le contrôle est retourné à la fonction appelante. Par exemple,

```MASM
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

Si un pointeur de frame est utilisé dans la fonction, la pile doit être réduite à son allocation fixe avant l’exécution de l’épilogue. Cette action n’est techniquement pas une partie de l’épilogue. Par exemple, l’épilogue suivant peut être utilisé pour annuler le prologue utilisé précédemment :

```MASM
    lea      RSP, -128[R13]
    ; epilogue proper starts here
    add      RSP, fixed-allocation-size
    pop      R13
    pop      R14
    pop      R15
    ret
```

Dans la pratique, lorsqu’un pointeur de frame est utilisé, il n’y a aucune bonne raison d’ajuster RSP en deux étapes. l’épilogue suivant est donc utilisé à la place :

```MASM
    lea      RSP, fixed-allocation-size - 128[R13]
    pop      R13
    pop      R14
    pop      R15
    ret
```

Ces formulaires sont les seuls à être autorisés pour un épilogue. Il doit se composer d’un `add RSP,constant` ou `lea RSP,constant[FPReg]`d’un, suivi d’une série de zéro ou plusieurs points de présence de Registre `return` de 8 `jmp`octets et d’un ou d’un. (Seul un sous- `jmp` ensemble d’instructions est autorisé dans l’épilogue. Le sous-ensemble est exclusivement la `jmp` classe d’instructions avec des références de mémoire ModRM où la valeur du champ mod ModRM est 00. L’utilisation d' `jmp` instructions dans l’épilogue avec la valeur de champ ModRM mod 01 ou 10 est interdite. Pour plus d’informations sur les références ModRM autorisées, consultez le tableau A-15 de l’architecture AMD x86-64 Guide de l’ouvrage manuel 3 : usage général et des instructions du système.) Aucun autre code ne peut apparaître. En particulier, rien ne peut être planifié dans un épilogue, y compris le chargement d’une valeur de retour.

Lorsqu’un pointeur de frame n’est pas utilisé, l’épilogue doit utiliser `add RSP,constant` pour libérer la partie fixe de la pile. Elle ne peut pas `lea RSP,constant[RSP]` utiliser à la place. Cette restriction existe afin que le code de déroulement ait moins de modèles à reconnaître lors de la recherche de épilogues.

Le respect de ces règles permet au code de déroulement de déterminer qu’un épilogue est en cours d’exécution et de simuler l’exécution du reste de l’épilogue pour permettre la recréation du contexte de la fonction appelante.

## <a name="see-also"></a>Voir aussi

[Conventions des logiciels x64](x64-software-conventions.md)
