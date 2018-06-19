---
title: Allocation de pile | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 098e51f2-eda6-40d0-b149-0b618aa48b47
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: caa6d435db98c7177cbf55b866bb8e5a4a110c1d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380600"
---
# <a name="stack-allocation"></a>Allocation de piles
Prologue d’une fonction est responsable de l’allocation d’espace de pile pour les variables locales, les registres enregistrés, les paramètres de la pile et paramètres de Registre.  
  
 La zone de paramètres est toujours en bas de la pile (même si alloca est utilisé), afin qu’il sera toujours adjacente à l’adresse de retour pendant un appel de fonction. Il contient au moins quatre entrées, mais toujours suffisamment d’espace pour contenir tous les paramètres requis par n’importe quelle fonction qui peut être appelée. Notez que l’espace est toujours alloué pour les paramètres de Registre, même si les paramètres proprement dits ne sont jamais hébergés dans la pile. un appelant est garanti que l’espace a été alloué pour tous ses paramètres. Adresses d’origine sont requises pour les arguments de Registre pour une zone contiguë soit disponible au cas où la fonction appelée doit prendre l’adresse de la liste d’arguments (va_list) ou un argument individuel. Cette zone fournit également un emplacement pratique pour enregistrer des arguments de Registre pendant l’exécution de la conversion de code et en tant qu’option de débogage (par exemple, il facilite les arguments rechercher pendant le débogage s’ils sont stockés à leur adresse d’origine dans le code de prologue). Même si la fonction appelée possède moins de 4 paramètres, ces 4 emplacements de pile sont en réalité détenus par la fonction appelée et peuvent être utilisés par la fonction appelée à d’autres fins que l’enregistrement des valeurs de Registre de paramètre.  Par conséquent, l’appelant peut enregistrer les informations dans cette région de pile dans un appel de fonction.  
  
 Si l’espace alloué dynamiquement (alloca) dans une fonction, un Registre non volatil doit être utilisé comme pointeur de frame pour marquer la base de la partie fixe de la pile et qui s’inscrivent doit être enregistré et initialisé dans le prologue. Notez que lorsque alloca est utilisé, les appels au même appelé à partir de l’appelant même peuvent avoir des adresses d’origine différentes pour leurs paramètres de Registre.  
  
 La pile est toujours conservée 16 octets aligné, sauf dans le prologue (par exemple, une fois que l’adresse de retour est l’objet d’un push) et à l’endroit indiqué dans [Types de fonction](../build/function-types.md) pour une certaine classe de fonctions de trame.  
  
 Voici un exemple de la disposition de pile où la fonction A appelle non terminaux fonction prologue de b a déjà alloué espace pour tous les paramètres de Registre et de pile requis par B en bas de la pile. Exécute un push de l’appel de l’adresse de retour et le prologue de B alloue de l’espace pour ses variables locales, les registres non volatils et l’espace requis pour appeler des fonctions. Si B utilise alloca, l’espace est alloué entre le Registre non volatiles/variables local zone de sauvegarde et de la zone paramètre de la pile.  
  
 ![Exemple de conversion AMD](../build/media/vcamd_conv_ex_5.png "vcAmd_conv_ex_5")  
  
 Lorsque la fonction B appelle une autre fonction, l’adresse de retour est placé juste en dessous de l’adresse personnelle pour RCX.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de la pile](../build/stack-usage.md)