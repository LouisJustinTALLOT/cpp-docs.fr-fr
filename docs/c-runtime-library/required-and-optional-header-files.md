---
title: Fichiers d'en-tête requis et facultatifs
description: Quand utiliser les fichiers d’en-tête requis et facultatifs de la bibliothèque Runtime C Microsoft.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- c.headers
helpviewer_keywords:
- include files, required in run time
- header files, required in run time
ms.assetid: f64d0bf5-e2c3-4b42-97d0-443b3d901d9f
ms.openlocfilehash: 79a45aaba5e2872b23e70f3fd276d6f3cae11167
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589807"
---
# <a name="required-and-optional-header-files"></a>Fichiers d'en-tête requis et facultatifs

La description de chaque routine d’exécution inclut une liste de fichiers include ou header (.H) obligatoires ou facultatifs pour cette routine. Les fichiers d’en-tête requis doivent être inclus afin d’obtenir la déclaration de fonction pour la routine ou une définition utilisée par une autre routine appelée en interne. Les fichiers d’en-tête facultatifs sont généralement inclus pour tirer parti des constantes prédéfinies, des définitions de type ou des macros inline. Le tableau suivant répertorie quelques exemples de contenu facultatif de fichier d’en-tête :

|Définition|Exemple|
|----------------|-------------|
|Définition de macro|Si une routine de bibliothèque est implémentée comme une macro, la définition de macro peut se trouver dans un fichier d’en-tête autre que le fichier d’en-tête de la routine d’origine. Par exemple, la macro `_toupper` est définie dans le fichier d’en-tête CTYPE.H, tandis que la fonction `toupper` est déclarée dans STDLIB.H.|
|Constante prédéfinie|De routines de bibliothèque font référence à des constantes qui sont définies dans les fichiers d’en-tête. Par exemple, la routine `_open` utilise des constantes comme `_O_CREAT`, qui est définie dans le fichier d’en-tête FCNTL.H.|
|Définition de types|Certaines routines de bibliothèque retournent une structure ou prennent une structure en tant qu’argument. Par exemple, les routines d’entrée/sortie de flux utilisent une structure de type `FILE`, qui est définie dans STDIO.H.|

Les fichiers d’en-tête de la bibliothèque Runtime fournissent des déclarations de fonction dans le style recommandé par la norme ANSI/ISO C. Le compilateur effectue la vérification du type sur toute référence de routine qui se produit après sa déclaration de fonction associée. Les déclarations de fonction sont particulièrement importantes pour les routines qui retournent une valeur d’un type autre que **`int`** , qui est la valeur par défaut. Les routines qui ne spécifient pas leur valeur de retour appropriée dans leur déclaration sont prises en compte par le compilateur pour retourner un **`int`** , ce qui peut provoquer des résultats inattendus. Consultez [Contrôle de type](../c-runtime-library/type-checking-crt.md) pour plus d’informations.

## <a name="see-also"></a>Voir aussi

[Fonctionnalités de la bibliothèque CRT](../c-runtime-library/crt-library-features.md)
