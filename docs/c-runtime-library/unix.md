---
title: UNIX | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: unix
dev_langs: C++
helpviewer_keywords:
- UNIX
- POSIX compatibility
- POSIX file names
- UNIX, compatibility
ms.assetid: 40792414-7a5b-415d-bfa8-2bfb1ebb3731
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8db5466439b72c4291383913451bcf5a0b415848
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="unix"></a>UNIX
Si vous prévoyez de porter vos programmes vers UNIX, suivez ces instructions :  
  
-   Ne supprimez pas les fichiers d’en-tête dans le sous-répertoire SYS. Vous pouvez placer les fichiers d’en-tête SYS ailleurs, si vous n’envisagez pas de porter vos programmes vers UNIX.  
  
-   Utilisez le séparateur de chemin d’accès compatible avec UNIX dans les routines qui acceptent des chaînes représentant des chemins d’accès et des noms de fichiers en tant qu’arguments. UNIX prend uniquement en charge la barre oblique (/) à cette fin, tandis que les systèmes d’exploitation Win32 prennent en charge à la fois la barre oblique inverse (\\) et la barre oblique (/). Par conséquent, cette documentation utilise les barres obliques compatibles avec UNIX comme délimiteur de chemin d’accès dans les instructions `#include`, par exemple. (Toutefois, l’interpréteur de commandes du système d’exploitation Windows, CMD.EXE, ne prend pas en charge la barre oblique dans les commandes entrées au niveau de l’invite de commandes.)  
  
-   Utilisez des chemins d’accès et des noms de fichiers qui fonctionnent correctement dans UNIX, qui est sensible à la casse. Le système de fichiers FAT dans les systèmes d’exploitation Win32 ne respecte pas la casse ; le système de fichiers NTFS préserve la casse pour les listes de répertoires, mais ignore la casse dans les recherches de fichiers et autres opérations système.  
  
    > [!NOTE]
    >  Dans cette version de Visual C++, les informations sur la compatibilité UNIX ont été supprimées des descriptions de fonction.  
  
## <a name="see-also"></a>Voir aussi  
 [Compatibilité](../c-runtime-library/compatibility.md)