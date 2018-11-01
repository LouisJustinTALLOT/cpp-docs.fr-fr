---
title: Procédure de déroulement
ms.date: 11/04/2016
ms.assetid: 82c5d0ca-70be-4d1a-a306-bfe01c29159f
ms.openlocfilehash: 2d68a5c3fb1cc2d18b587d1419b0103d02b35a7f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523096"
---
# <a name="unwind-procedure"></a>Procédure de déroulement

Le tableau des codes de déroulement est trié dans l’ordre décroissant. Lorsqu’une exception se produit, le contexte complet est stocké par le système d’exploitation dans un enregistrement de contexte. La logique de répartition d’exception est appelée, qui exécute plusieurs fois les étapes suivantes pour rechercher un gestionnaire d’exceptions.

1. Utilisez le RIP actuel stocké dans l’enregistrement de contexte pour rechercher une entrée de table RUNTIME_FUNCTION qui décrit la fonction active (ou une partie de la fonction, dans le cas d’entrées UNWIND_INFO chaînées).

1. Si aucune entrée de table de fonction est trouvée, puis il se trouve dans une fonction de la feuille, et RSP adresse directement le pointeur de retour. Le pointeur de retour à [RSP] est stocké dans le contexte mis à jour, le RSP simulé est incrémenté de 8 et l’étape 1 est répétée.

1. Si une entrée de table de fonction est trouvée, RIP peut se trouver dans trois régions a) dans un épilogue, b) dans le prologue ou c) dans le code qui peut être couvert par un gestionnaire d’exceptions.

   - Cas un) si le protocole RIP est dans un épilogue, puis contrôle quitte la fonction, il ne peut y avoir aucun gestionnaire d’exceptions associé à cette exception pour cette fonction et les effets de l’épilogue doivent continuer à utiliser le contexte de la fonction d’appelant de calcul. Pour déterminer si le protocole RIP est dans un épilogue, le flux de code à partir de RIP sur est examiné. Ce flux de code peut être mis en correspondance avec la partie finale d’un épilogue, il se trouve dans un épilogue, puis sur la partie restante de l’épilogue est simulée, avec l’enregistrement de contexte mis à jour en tant que chaque instruction est traitée. Après cela, l’étape 1 est répétée.

   - Cas b) si le protocole RIP se trouve dans le prologue, contrôle n’a pas accédé à la fonction, il ne peut y avoir aucun gestionnaire d’exceptions associé à cette exception pour cette fonction et les effets du prologue doivent être annulés pour calculer le contexte de la fonction d’appelant. Le protocole RIP se trouve dans le prologue si la distance entre le début de la fonction et le protocole RIP est inférieure ou égale à la taille du prologue encodée dans les informations de déroulement. Les effets du prologue sont déroulés en recherchant, dans le tableau de codes de déroulement pour la première entrée avec un décalage inférieur ou égal à l’offset du RIP à partir du début de la fonction, puis en annulant l’effet de tous les éléments restants dans le tableau des codes de déroulement. Étape 1 est ensuite répétée.

   - Cas c) si le protocole RIP n’est pas dans un prologue ou épilogue et la fonction a un gestionnaire d’exceptions (UNW_FLAG_EHANDLER est défini), alors le gestionnaire spécifique au langage est appelé. Le Gestionnaire d’analyse ses données et appelle des fonctions comme il convient de filtre. Gestionnaire spécifique au langage peut retourner que l’exception a été gérée ou que la recherche doit être poursuivie. Elle peut également initier un déroulement directement.

1. Si le gestionnaire spécifique au langage retourne un état géré, l’exécution se poursuite à l’aide de l’enregistrement de contexte d’origine.

1. S’il n’existe aucun gestionnaire spécifique au langage ou le gestionnaire renvoie l’état « continuer la recherche », l’enregistrement de contexte doit être déroulé à l’état de l’appelant. Pour cela, vous devez traiter tous les éléments du tableau du code de déroulement, annulant l’effet de chacune. Étape 1 est ensuite répétée.

Lorsqu’il est chaîné déroulement info est impliqué, ces étapes de base sont toujours suivies. La seule différence est que, tandis que de parcourir le tableau des codes de déroulement pour dérouler les effets d’un prologue, une fois que la fin du tableau est atteinte, il est ensuite lié les informations de déroulement parent et le tableau de code de déroulement ensemble qu’il contient est parcouru. Cette liaison se poursuit jusqu'à ce qu’informations de déroulement sans l’indicateur UNW_CHAINED_INFO et terminé de parcourir son tableau des codes de déroulement.

Données de déroulement le plus petit ensemble de 8 octets. Cela représente une fonction qui a affecté uniquement 128 octets de pile ou moins et éventuellement enregistré un Registre non volatil. Il s’agit également la taille de chaînées structure d’informations pour un prologue de longueur nulle avec sans code de déroulement de déroulement.

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions (x64)](../build/exception-handling-x64.md)