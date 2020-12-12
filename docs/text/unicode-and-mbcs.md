---
description: 'En savoir plus sur les éléments suivants : Unicode et MBCS'
title: Unicode et MBCS
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], Unicode
- MFC [C++], character sets
- character sets [C++], multibyte
- run-time libraries [C++], language portability
- character sets [C++], Unicode
- Unicode [C++], MFC and C run-time functions
- multibyte characters [C++]
- runtime [C++], language portability
ms.assetid: 677baec6-71b4-4579-94df-64f18bc117c4
ms.openlocfilehash: 4fc5afc447612a3f08067185072cd4f116ab80c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114973"
---
# <a name="unicode-and-mbcs"></a>Unicode et MBCS

La bibliothèque Microsoft Foundation Classes (MFC), la bibliothèque Runtime C pour Visual C++ et l’environnement de développement Visual C++ sont activés pour faciliter la programmation internationale. Elles fournissent :

- Prise en charge de la norme Unicode sur Windows. Unicode est la norme actuelle et doit être utilisée dans la mesure du possible.

   Unicode est un encodage de caractères de 16 bits, fournissant suffisamment de codages pour tous les langages. Tous les caractères ASCII sont inclus en caractères étendus dans Unicode.

- Prise en charge d’une forme de jeu de caractères multioctets (MBCS) appelée jeu de caractères codés sur deux octets (DBCS) sur toutes les plateformes.

   Les caractères DBCS sont composés de 1 ou 2 octets. Certaines plages d’octets sont réservées pour une utilisation en tant qu’octets de tête. Un octet de tête spécifie qu’il et l’octet de fin suivant forment un caractère unique de 2 octets. Vous devez effectuer le suivi des octets de tête en octets. Dans un jeu de caractères multioctets, les octets de tête sont compris dans une plage et les octets de fin dans une autre. Lorsque ces plages se chevauchent, il peut être nécessaire d’évaluer le contexte pour déterminer si un octet donné fonctionne comme un octet de tête ou un octet de fin.

- Prise en charge des outils qui simplifient la programmation MBCS des applications écrites pour les marchés internationaux.

   Lorsqu’il est exécuté sur une version MBCS du système d’exploitation Windows, le système de développement Visual C++, y compris l’éditeur de code source intégré, le débogueur et les outils en ligne de commande, est entièrement compatible MBCS. Pour plus d’informations, consultez [prise en charge MBCS dans Visual C++](../text/mbcs-support-in-visual-cpp.md).

> [!NOTE]
> Dans cette documentation, MBCS est utilisé pour décrire toute la prise en charge non-Unicode pour les caractères multioctets. Dans Visual C++, MBCS signifie toujours DBCS. Les jeux de caractères de plus de 2 octets ne sont pas pris en charge.

Par définition, le jeu de caractères ASCII est un sous-ensemble de tous les jeux de caractères multioctets. Dans de nombreux jeux de caractères multioctets, chaque caractère de la plage 0x00-0x7F est identique au caractère qui a la même valeur dans le jeu de caractères ASCII. Par exemple, dans les chaînes de caractères ASCII et MBCS, le caractère NULL de 1 octet (' \ 0 ') a la valeur 0x00 et indique le caractère null de fin.

## <a name="see-also"></a>Voir aussi

[Texte et chaînes](../text/text-and-strings-in-visual-cpp.md)<br/>
[Activation internationale](../text/international-enabling.md)
