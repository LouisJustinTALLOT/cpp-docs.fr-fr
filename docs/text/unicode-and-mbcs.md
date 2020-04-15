---
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
ms.openlocfilehash: 063c8b39ee0d29403b382b57a236f2a3e8759e3f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375753"
---
# <a name="unicode-and-mbcs"></a>Unicode et MBCS

La bibliothèque Microsoft Foundation Classes (MFC), la bibliothèque C run-time pour Visual CMD et l’environnement de développement Visual CMD sont autorisés à vous aider dans votre programmation internationale. Elles fournissent :

- Prise en charge de la norme Unicode sur Windows. Unicode est la norme actuelle et doit être utilisé dans la mesure du possible.

   Unicode est un codage de caractère 16 bits, fournissant suffisamment d’encodages pour toutes les langues. Tous les caractères ASCII sont inclus dans Unicode en tant que caractères élargis.

- Prise en charge d’une forme d’ensemble de caractères multioctets (MBCS) appelé ensemble de caractères double-byte (DBCS) sur toutes les plates-formes.

   Les caractères DBCS sont composés de 1 ou 2 octets. Certaines gammes d’octets sont mises de côté pour être utilisées comme octets de plomb. Un byte de plomb précise qu’il et le byte sentier suivant comprennent un seul caractère de 2-byte-large. Vous devez garder une trace des octets qui sont des octets en plomb. Dans un jeu de caractères multioctets, les octets de tête sont compris dans une plage et les octets de fin dans une autre. Lorsque ces plages se chevauchent, il peut être nécessaire d’évaluer le contexte pour déterminer si un byte donné fonctionne comme un byte de plomb ou un byte de sentier.

- Soutien aux outils qui simplifient la programmation des applications de MBCS écrites pour les marchés internationaux.

   Lorsqu’il est exécuté sur une version MBCS du système d’exploitation Windows, le système de développement Visual CMD — y compris l’éditeur de code source intégré, le débbuggeur et les outils de ligne de commande — est entièrement compatible MBCS. Pour plus d’informations, voir [MBCS Support in Visual C .](../text/mbcs-support-in-visual-cpp.md)

> [!NOTE]
> Dans cette documentation, MBCS est utilisé pour décrire tous les soutiens non-Unicode pour les caractères multioctets. Dans Visual C, MBCS signifie toujours DBCS. Les ensembles de caractères plus larges que 2 octets ne sont pas pris en charge.

Par définition, l’ensemble de caractères ASCII est un sous-ensemble de tous les ensembles multioctets. Dans de nombreux jeux de caractères multioctets, chaque caractère de la plage 0x00-0x7F est identique au caractère qui a la même valeur dans le jeu de caractères ASCII. Par exemple, dans les deux chaînes de caractères ASCII et MBCS, le caractère NULL de 1-byte ('0') a une valeur de 0x00 et indique le caractère nul de fin.

## <a name="see-also"></a>Voir aussi

[Texte et chaînes](../text/text-and-strings-in-visual-cpp.md)<br/>
[Habilitation internationale](../text/international-enabling.md)
