---
title: UNIX
description: Instructions pour le portage de votre programme vers UNIX.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- unix
helpviewer_keywords:
- UNIX
- POSIX compatibility
- POSIX file names
- UNIX, compatibility
ms.assetid: 40792414-7a5b-415d-bfa8-2bfb1ebb3731
ms.openlocfilehash: 3975db2407943b329fa7eded0d72d63524428210
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765216"
---
# <a name="unix"></a>UNIX

Si vous prévoyez de porter vos programmes vers UNIX, suivez ces instructions :

- Ne supprimez pas les fichiers d’en-tête du sous-répertoire SYS. Vous pouvez placer les fichiers d’en-tête SYS ailleurs uniquement si vous n’envisagez pas de transporter vos programmes vers UNIX.

- Utilisez le séparateur de chemin d’accès compatible avec UNIX dans les routines qui acceptent des chaînes représentant des chemins d’accès et des noms de fichiers en tant qu’arguments. UNIX prend en charge uniquement la barre oblique (/) à cet effet, mais les systèmes d’exploitation Win32 prennent en charge la barre oblique inverse ( \\ ) et la barre oblique (/). Cette documentation utilise des barres obliques compatibles UNIX comme séparateurs de chemin d’accès dans `#include` les instructions, par exemple. (Toutefois, l’interface de commande du système d’exploitation Windows, CMD.EXE, ne prend pas en charge la barre oblique dans les commandes entrées à l’invite de commandes.)

- Utilisez des chemins d’accès et des noms de fichiers qui fonctionnent correctement dans UNIX, qui respecte la casse. Le système de fichiers FAT (File Allocation Table) dans les systèmes d’exploitation Win32 n’est pas sensible à la casse. Le système de fichiers NTFS préserve la casse pour les listes de répertoires, mais ignore la casse dans les recherches de fichiers et les autres opérations système.

> [!NOTE]
> Dans cette version de Visual C++, les informations sur la compatibilité UNIX ont été supprimées des descriptions de fonction.

## <a name="see-also"></a>Voir aussi

[Compatibilité](../c-runtime-library/compatibility.md)
