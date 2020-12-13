---
description: 'En savoir plus sur : erreur irrécupérable C1084'
title: Erreur irrécupérable C1084
ms.date: 11/04/2016
f1_keywords:
- C1084
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
ms.openlocfilehash: 6a3221bb894c0b320642a923d9552a207a2ff9ed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145312"
---
# <a name="fatal-error-c1084"></a>Erreur irrécupérable C1084

Impossible de lire le fichier 'TypeFichier' : 'fichier' : message

Cette erreur résulte généralement de l'échec d'un appel à une API système interne effectué par le compilateur. Le message qui s’affiche lorsque cette erreur est rencontrée est souvent généré par [_wcserror_s](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) ou [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage).

La procédure ci-dessous peut aider à résoudre l'erreur C1084 :

- Assurez-vous que le fichier spécifié existe.

- Assurez-vous que les autorisations appropriées sont définies afin de pouvoir accéder au fichier spécifié.

- Assurez-vous que la syntaxe de la ligne de commande respecte les règles décrites dans [syntaxe de Command-Line du compilateur](../../build/reference/compiler-command-line-syntax.md).

- Assurez-vous que les variables d’environnement **tmp** et **temp** sont correctement définies, ainsi que les autorisations appropriées pour accéder aux répertoires auxquels ces variables d’environnement font référence. Assurez-vous également que les lecteurs référencés par les variables d’environnement **tmp** et **temp** contiennent une quantité d’espace libre suffisante.

- Si le message indique « numéro de fichier incorrect », le fichier spécifié était peut-être en cours de fermeture au premier plan alors que la compilation se déroulait en arrière-plan.

Après avoir effectué les diagnostics ci-dessus, effectuez un nettoyage de build.
