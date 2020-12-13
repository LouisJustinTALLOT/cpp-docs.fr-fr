---
description: En savoir plus sur les flux de sortie
title: Flux de sortie
ms.date: 11/04/2016
helpviewer_keywords:
- output streams
ms.assetid: b49410e3-5caa-4153-9d0d-c4266408dc83
ms.openlocfilehash: ec09a6bee1bcd2f329522b61950f3d051fb57889
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340864"
---
# <a name="output-streams"></a>Flux de sortie

Un objet de flux de sortie sert de destination pour les octets. Les trois principales classes de flux de sortie sont `ostream`, `ofstream` et `ostringstream`.

La classe `ostream`, via la classe dérivée `basic_ostream`, prend en charge les objets de flux prédéfinis suivants :

- Objet de flux de sortie standard `cout`

- Erreur standard `cerr` avec une mise en mémoire tampon limitée

- Objet `clog` semblable à `cerr`, mais avec une mise en mémoire tampon complète

Les objets sont rarement construits à partir de la classe `ostream`. Les objets prédéfinis sont généralement utilisés. Dans certains cas, vous pouvez réassigner les objets prédéfinis après le démarrage du programme. La classe `ostream` peut être configurée pour des opérations avec ou sans mise en mémoire tampon. Son utilisation est recommandée pour la sortie séquentielle en mode texte. Toutes les fonctionnalités de la classe de base, `ios`, sont incluses dans `ostream`. Si vous construisez un objet de classe `ostream`, vous devez spécifier un objet `streambuf` pour le constructeur.

La classe `ofstream` prend en charge la sortie de fichier de disque. Si vous devez utiliser un disque de sortie uniquement, construisez un objet de classe `ofstream`. Vous pouvez spécifier si les objets `ofstream` acceptent les données binaires ou en mode texte lors de la construction de l’objet `ofstream` ou lors de l’appel de la fonction membre `open` de l’objet. De nombreuses fonctions membres et options de mise en forme s’appliquent aux objets `ofstream`, et toutes les fonctionnalités des classes de base `ios` et `ostream` sont fournies.

Si vous spécifiez un nom de fichier dans le constructeur, ce fichier s’ouvre automatiquement quand l’objet est construit. Sinon, vous pouvez utiliser la fonction membre `open` après avoir appelé le constructeur par défaut.

De la même façon que la fonction runtime `sprintf_s`, la classe `ostringstream` prend en charge la sortie vers des chaînes en mémoire. Pour créer une chaîne en mémoire avec la mise en forme de flux d’E/S, construisez un objet de classe `ostringstream`.

## <a name="in-this-section"></a>Dans cette section

[Construction d’objets de flux de sortie](../standard-library/constructing-output-stream-objects.md)

[Utilisation des opérateurs d’insertion et contrôle du format](../standard-library/using-insertion-operators-and-controlling-format.md)

[Fonctions membres de flux de fichier de sortie](../standard-library/output-file-stream-member-functions.md)

[Effets de la mise en mémoire tampon](../standard-library/effects-of-buffering.md)

[Fichiers de sortie binaires](../standard-library/binary-output-files.md)

[Surcharge de l’opérateur << pour vos propres classes](../standard-library/overloading-the-output-operator-for-your-own-classes.md)

[Écriture de vos propres manipulateurs sans arguments](../standard-library/writing-your-own-manipulators-without-arguments.md)

## <a name="see-also"></a>Voir aussi

[ofstream](../standard-library/basic-ofstream-class.md)\
[ostringstream](../standard-library/basic-ostringstream-class.md)\
[iostream, programmation](../standard-library/iostream-programming.md)
