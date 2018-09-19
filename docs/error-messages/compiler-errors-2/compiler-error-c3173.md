---
title: Erreur du compilateur C3173 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3173
dev_langs:
- C++
helpviewer_keywords:
- C3173
ms.assetid: edf79e10-e8cf-4f76-8d33-ab9d05e974e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21a02ae1fcf4aff9636445979a81ef0a02ab5cb1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053022"
---
# <a name="compiler-error-c3173"></a>Erreur du compilateur C3173

incompatibilité de version dans la fusion idl

Cette erreur se produit lorsqu’un fichier objet contient un idl incorporé qui a été généré avec une version précédente du compilateur. Le compilateur encode un numéro de version pour vous assurer que le même compilateur utilisé pour générer le contenu idl qui est incorporé dans les fichiers .obj est également le même compilateur utilisé pour fusionner l’idl incorporé.

Mettre à jour votre installation de Visual C++ afin que tous les outils sont à partir de la dernière version publiée.