---
title: Erreur irrécupérable C1084
ms.date: 11/04/2016
f1_keywords:
- C1084
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
ms.openlocfilehash: 8c90616165a7b47d4251ace998fd49c613f244b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208813"
---
# <a name="fatal-error-c1084"></a>Erreur irrécupérable C1084

Impossible de lire le fichier 'TypeFichier' : 'fichier' : message

Cette erreur résulte généralement de l'échec d'un appel à une API système interne effectué par le compilateur. Le message affiché lorsque cette erreur est rencontrée est souvent généré à l’aide [_wcserror_s](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) ou [FormatMessage](/windows/desktop/api/winbase/nf-winbase-formatmessage).

La procédure ci-dessous peut aider à résoudre l'erreur C1084 :

- Assurez-vous que le fichier spécifié existe.

- Assurez-vous que les autorisations appropriées sont définies afin de pouvoir accéder au fichier spécifié.

- Vérifiez que la syntaxe de ligne de commande respecte les règles décrites sous [du compilateur de ligne de commande syntaxe](../../build/reference/compiler-command-line-syntax.md).

- Assurez-vous que les variables d’environnement **TMP** et **TEMP** sont correctement ensemble, ainsi que les autorisations appropriées pour accéder aux répertoires ces variables d’environnement font référence. Vérifiez que les lecteurs référencés par le **TMP** et **TEMP** variables d’environnement contiennent une quantité adéquate d’espace libre.

- Si le message indique « numéro de fichier incorrect », le fichier spécifié était peut-être en cours de fermeture au premier plan alors que la compilation se déroulait en arrière-plan.

Après avoir effectué les diagnostics ci-dessus, effectuez un nettoyage de build.