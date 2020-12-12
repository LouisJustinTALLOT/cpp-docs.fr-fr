---
description: En savoir plus sur:/REBASE
title: /REBASE
ms.date: 11/04/2016
f1_keywords:
- /rebase
helpviewer_keywords:
- base addresses [C++]
- -REBASE editbin option
- REBASE editbin option
- DLLs [C++], linking
- executable files [C++], base address
- /REBASE editbin option [C++]
ms.assetid: 3f89d874-af5c-485b-974b-fd205f6e1a4b
ms.openlocfilehash: 6cbbf0a21bd9306167fb165b63c22e810518e161
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225334"
---
# <a name="rebase"></a>/REBASE

```
/REBASE[:modifiers]
```

## <a name="remarks"></a>Notes

Cette option définit les adresses de base pour les fichiers spécifiés. EDITBIN affecte de nouvelles adresses de base dans un espace d’adressage contigu en fonction de la taille de chaque fichier, arrondie au 64 Ko le plus proche. Pour plus d’informations sur les adresses de base, consultez l’option de l’éditeur de liens [adresse de base](base-base-address.md) (/base).

Spécifiez les fichiers exécutables et les dll du programme dans l’argument *Files* sur la ligne de commande EDITBIN dans l’ordre dans lequel ils doivent être basés. Vous pouvez éventuellement spécifier un ou plusieurs *modificateurs*, séparés par une virgule (**,**) :

|Modificateur|Action|
|--------------|------------|
|**Base =**<em>adresse</em>|Fournit une adresse de début pour la réassignation des adresses de base aux fichiers. Spécifiez l' *adresse* en notation décimale ou de langage C. Si BASE n’est pas spécifié, l’adresse de base de départ par défaut est 0x400000. Si le paramètre bas est utilisé, BASE doit être spécifié et l' *adresse* définit la fin de la plage d’adresses de base.|
|**BASEFILE**|Crée un fichier nommé COFFBASE.TXT, qui est un fichier texte au format attendu par l’option/BASE du lien.|
|**BAISSE**|Indique à EDITBIN de réassigner les adresses de base à partir d’une adresse de fin. Les fichiers sont réaffectés dans l’ordre spécifié, le premier fichier se trouvant dans l’adresse la plus élevée possible en dessous de la fin de la plage d’adresses. BASE doit être utilisé avec la valeur inférieure pour garantir un espace d’adressage suffisant pour la base des fichiers. Pour déterminer l’espace d’adressage requis par les fichiers spécifiés, exécutez EDITBIN avec/REBASE sur les fichiers et ajoutez 64 Ko à la taille totale affichée.|

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](editbin-options.md)
