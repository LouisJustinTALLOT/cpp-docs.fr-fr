---
title: Stockage des adresses | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- storage [C++], addresses
- addresses [C++], storage of
ms.assetid: 423b2402-b847-4788-ad70-943b7c9c5c8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d892aac81efa8c2628c8662558b52cc1eb2e21c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32386509"
---
# <a name="storage-of-addresses"></a>Stockage des adresses
La quantité de stockage requis pour une adresse et la signification de l'adresse dépendent de l'implémentation du compilateur. Les pointeurs vers des types différents ne sont pas garantis avoir la même longueur. Par conséquent, **sizeof(char \*)** n'est pas nécessairement égal à **sizeof(int \*)**.  
  
 **Section spécifique à Microsoft**  
  
 Pour le compilateur C Microsoft, **sizeof(char \*)** est égal à **sizeof(int \*)**.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Déclarations de pointeur](../c-language/pointer-declarations.md)