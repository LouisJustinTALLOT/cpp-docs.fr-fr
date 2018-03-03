---
title: "Contrôle des flux | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Controlling Streams
dev_langs:
- C++
helpviewer_keywords:
- streams, controlling
- controlling streams
- streams
ms.assetid: 267e9013-9afc-45f6-91e3-ca093230d9d9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d6b2678add561eda41a7426a840b9c4ad074301
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="controlling-streams"></a>Contrôle des flux
[fopen](../c-runtime-library/reference/fopen-wfopen.md) retourne l’adresse d’un objet de type `FILE`. Vous utilisez cette adresse en tant qu’argument `stream` pour plusieurs fonctions de bibliothèque afin d’effectuer diverses opérations sur un fichier ouvert. Pour un flux d’octets, toutes les entrées surviennent comme si chaque caractère était lu en appelant [fgetc](../c-runtime-library/reference/fgetc-fgetwc.md) et toutes les sorties surviennet comme si chaque caractère était écrit en appelant [fputc](../c-runtime-library/reference/fputc-fputwc.md). Pour un flux larges, toutes les entrées surviennent comme si chaque caractère était lu en appelant [fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md) et toutes les sorties surviennet comme si chaque caractère était écrit en appelant [fputwc](../c-runtime-library/reference/fputc-fputwc.md).  
  
 Vous pouvez fermer un fichier en appelant [fclose](../c-runtime-library/reference/fclose-fcloseall.md), après quoi l’adresse de l’objet `FILE` n’est pas valide.  
  
 Un objet `FILE` stocke l’état d’un flux de données, y compris :  
  
-   Un indicateur d’erreur défini sur une valeur différente de zéro par une fonction qui rencontre une erreur de lecture ou d’écriture.  
  
-   Un indicateur de fin de fichier défini sur une valeur différente de zéro par une fonction qui rencontre la fin du fichier lors de la lecture.  
  
-   Un indicateur de position de fichier spécifie l’octet suivant dans le flux à lire ou écrire, si le fichier peut prendre en charge les demandes de positionnement.  
  
-   Un [état de flux](../c-runtime-library/stream-states.md) spécifie si le flux acceptera les lectures ou écritures, et si le flux de données est détaché, orienté octet ou orienté large.  
  
-   Un état de conversion se souvient de l’état de n’importe quel caractère multioctet partiellement assemblé ou généré généralisé, ainsi que n’importe quel état de décalage pour la séquence d’octets dans le fichier).  
  
-   Une mémoire tampon de fichier spécifie l’adresse et la taille d’un objet de tableau que les fonctions de bibliothèque peuvent utiliser pour améliorer les performances des opérations de lecture et d’écriture dans le flux.  
  
 Ne modifiez pas de valeur stockée dans un objet `FILE` ou dans une mémoire tampon de fichier que vous spécifiez pour une utilisation avec cet objet. Vous ne pouvez pas copier un objet `FILE` et utiliser de façon portable l’adresse de la copie comme un argument `stream` pour une fonction de bibliothèque.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers et flux](../c-runtime-library/files-and-streams.md)