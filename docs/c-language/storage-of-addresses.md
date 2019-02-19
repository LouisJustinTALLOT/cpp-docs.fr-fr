---
title: Stockage des adresses
ms.date: 11/04/2016
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
ms.openlocfilehash: 47b09ab6cd0b2045206daaee4badad32858ff934
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148736"
---
# <a name="storage-of-addresses"></a>Stockage des adresses

La quantité de stockage requis pour une adresse et la signification de l'adresse dépendent de l'implémentation du compilateur. Les pointeurs vers des types différents ne sont pas garantis avoir la même longueur. Par conséquent, **sizeof(char \*)** n'est pas nécessairement égal à **sizeof(int \*)**.

**Section spécifique à Microsoft**

Pour le compilateur C Microsoft, **sizeof(char \*)** est égal à **sizeof(int \*)**.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Déclarations de pointeur](../c-language/pointer-declarations.md)
