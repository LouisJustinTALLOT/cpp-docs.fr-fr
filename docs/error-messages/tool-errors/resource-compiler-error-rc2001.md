---
title: Erreur RC2001 du compilateur de ressources | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2001
dev_langs:
- C++
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ef1fd5d29fc5784ee418a8456cacec37e943b73
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322417"
---
# <a name="resource-compiler-error-rc2001"></a>Erreur RC2001 du compilateur de ressources 
saut de ligne dans la constante  
  
 Une constante de chaîne se poursuivie sur une seconde ligne, sans utilisation d’une barre oblique inverse (**\\**) ou ouverture et fermeture des guillemets doubles (**»**).  
  
 Pour interrompre une constante de chaîne sur deux lignes dans le fichier source, effectuez l’une des opérations suivantes :  
  
-   Fin de la première ligne avec le caractère de continuation de ligne, une barre oblique inverse.  
  
-   Fermez la chaîne sur la première ligne par un guillemet double et ouvrez la chaîne sur la ligne suivante avec un autre guillemet.  
  
 Il n’est pas suffisant mettre fin à la première ligne par \n, la séquence d’échappement pour incorporer un caractère de saut de ligne dans une constante de chaîne.