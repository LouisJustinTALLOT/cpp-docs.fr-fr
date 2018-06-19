---
title: Flux d’entrée | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- input streams
- input stream objects
ms.assetid: f14d8954-8f8c-4c3c-8b99-14ddb3683f94
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3dff2e0bb0ee070b8b90ca3896d7bf8114ca918
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845568"
---
# <a name="input-streams"></a>Flux d'entrée

Un objet de flux d’entrée est une source d’octets. Les trois classes de flux d’entrée les plus importantes sont [istream](../standard-library/basic-istream-class.md), [ifstream](../standard-library/basic-ifstream-class.md) et [istringstream](../standard-library/basic-istringstream-class.md).

La classe `istream` convient particulièrement à l’entrée de texte en mode séquentiel. Vous pouvez configurer des objets de classe `istream` pour des opération mises en mémoire tampon ou non. Toutes les fonctionnalités de la classe de base, `ios`, sont incluses dans `istream`. Vous serez rarement amené à construire des objets à partir de la classe `istream`. Au lieu de cela, vous utiliserez généralement l’objet `cin` prédéfini, qui est en fait un objet de classe [ostream](../standard-library/basic-ostream-class.md). Dans certains cas, vous pouvez affecter `cin` à d’autres objets de flux après le démarrage du programme.

La classe `ifstream` prend en charge l’entrée de fichier de disque. Si vous avez besoin d’un fichier de disque « entrée uniquement », construisez un objet de classe `ifstream`. Vous pouvez spécifier des données binaires ou en mode texte. Si vous spécifiez un nom de fichier dans le constructeur, le fichier s’ouvre automatiquement quand l’objet est construit. Sinon, vous pouvez utiliser la fonction `open` après avoir appelé le constructeur par défaut. De nombreuses fonctions membres et options de mise en forme s’appliquent aux objets `ifstream`. Toutes les fonctionnalités des classes de base `ios` et `istream` sont incluses dans `ifstream`.

Comme la fonction de bibliothèque `sscanf_s`, la classe `istringstream` prend en charge l’entrée à partir de chaînes en mémoire. Pour extraire des données à partir d’un tableau de caractères ayant une marque de fin Null, allouez et initialisez la chaîne, puis construisez un objet de classe `istringstream`.

## <a name="in-this-section"></a>Dans cette section

[Construction d’objets de flux d’entrée](../standard-library/constructing-input-stream-objects.md)

[Utilisation d’opérateurs d’extraction](../standard-library/using-extraction-operators.md)

[Tester les erreurs d’extraction](../standard-library/testing-for-extraction-errors.md)

[Manipulateurs de flux d’entrée](../standard-library/input-stream-manipulators.md)

[Fonctions membres de flux d’entrée](../standard-library/input-stream-member-functions.md)

[Surcharge de l’opérateur >> pour vos propres classes](../standard-library/overloading-the-input-operator-for-your-own-classes.md)

## <a name="see-also"></a>Voir aussi

[iostream, programmation](../standard-library/iostream-programming.md)<br/>
