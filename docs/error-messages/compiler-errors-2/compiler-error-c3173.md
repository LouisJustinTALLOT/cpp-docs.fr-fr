---
title: Erreur du compilateur C3173 | Documents Microsoft
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
ms.openlocfilehash: ef35c534ac834779da15fce99e8c82b94bd445e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33248073"
---
# <a name="compiler-error-c3173"></a>Erreur du compilateur C3173
incompatibilité de version dans la fusion idl  
  
 Cette erreur se produit lorsqu’un fichier objet contient un idl incorporé qui a été généré avec une version antérieure du compilateur. Le compilateur encode un numéro de version pour vous assurer que le même compilateur utilisé pour générer le contenu idl qui est incorporé dans les fichiers .obj est également du compilateur utilisé pour fusionner l’idl incorporé.  
  
 Mettre à jour votre installation Visual C++ afin que tous les outils sont à partir de la dernière version publiée.