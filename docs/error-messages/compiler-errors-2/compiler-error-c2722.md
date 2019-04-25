---
title: Erreur du compilateur C2722
ms.date: 11/04/2016
f1_keywords:
- C2722
helpviewer_keywords:
- C2722
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
ms.openlocfilehash: 4274ac6ec33e0176f998fcf5a2b3efd570a4009f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383033"
---
# <a name="compiler-error-c2722"></a>Erreur du compilateur C2722

' :: opérateur ' : non conforme après une commande operator ; Utilisez 'operator opérateur'

Un `operator` redéfinitions de l’instruction `::new` ou `::delete`. Le `new` et `delete` opérateurs sont globales, par conséquent, l’opérateur de résolution de portée (`::`) n’a aucune signification. Supprimez l’opérateur `::` .