---
title: Erreur irrécupérable C1084 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1084
dev_langs:
- C++
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7266a2158c3e6ccd02ea82de22c6f90a8b6363d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229387"
---
# <a name="fatal-error-c1084"></a>Erreur irrécupérable C1084
Impossible de lire le fichier 'TypeFichier' : 'fichier' : message  
  
 Cette erreur résulte généralement de l'échec d'un appel à une API système interne effectué par le compilateur. Le message affiché lorsque cette erreur se produit est souvent généré par le [_wcserror_s](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) ou [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351.aspx).  
  
 La procédure ci-dessous peut aider à résoudre l'erreur C1084 :  
  
-   Assurez-vous que le fichier spécifié existe.  
  
-   Assurez-vous que les autorisations appropriées sont définies afin de pouvoir accéder au fichier spécifié.  
  
-   Vérifiez que la syntaxe de ligne de commande respecte les règles détaillées dans [syntaxe de ligne de commande du compilateur](../../build/reference/compiler-command-line-syntax.md).  
  
-   Assurez-vous que les variables d’environnement **TMP** et **TEMP** sont correctement ensemble, ainsi que les autorisations appropriées pour accéder à ces variables d’environnement font référence aux répertoires. Vérifiez que les lecteurs référencés par le **TMP** et **TEMP** variables d’environnement contiennent une quantité adéquate d’espace libre.  
  
-   Si le message indique « numéro de fichier incorrect », le fichier spécifié était peut-être en cours de fermeture au premier plan alors que la compilation se déroulait en arrière-plan.  
  
 Après avoir effectué les diagnostics ci-dessus, effectuez un nettoyage de build.