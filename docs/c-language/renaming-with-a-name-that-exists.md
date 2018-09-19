---
title: Remplacement d'un nom par un nom qui existe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: fc2a8f29-f757-4ce0-8d7f-7f8cff7f49ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 10b9a9c4e42356a087c8cb6c10a470ba68acd4ba
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067752"
---
# <a name="renaming-with-a-name-that-exists"></a>Remplacement d'un nom par un nom qui existe

**ANSI 4.9.4.2** Effet s'il existe un fichier avec le nouveau nom avant un appel à la fonction **rename**

Si vous essayez de renommer un fichier en utilisant un nom qui existe déjà, la fonction **rename** échoue et retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi

[Fonctions des bibliothèques](../c-language/library-functions.md)