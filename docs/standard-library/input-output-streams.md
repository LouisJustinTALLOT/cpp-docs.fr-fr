---
title: Flux d’entrée-sortie
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], stream
- stream I/O
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
ms.openlocfilehash: d426baacb52095ab2d933263fdac8e312fc29558
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580220"
---
# <a name="inputoutput-streams"></a>Flux d'entrée/sortie

`basic_iostream`, qui est défini dans le fichier d’en-tête \<istream>, est le modèle de classe qui gère les flux d’E/S de caractères d’entrée et de sortie.

Il existe deux typedefs qui définissent des spécialisations de `basic_iostream` propres aux caractères et peuvent aider à améliorer la lisibilité du code : `iostream` (à ne pas confondre avec le fichier d’en-tête \<iostream>) est un flux d’E/S basé sur `basic_iostream<char>` ; `wiostream` est un flux d’E/S basé sur `basic_iostream<wchar_t>`.

Pour plus d’informations, consultez [basic_iostream, classe](../standard-library/basic-iostream-class.md), [iostream](../standard-library/basic-iostream-class.md) et [wiostream](../standard-library/basic-iostream-class.md).

Le modèle de classe `basic_fstream` dérive de `basic_iostream`. Il sert à transmettre des données de caractères vers et à partir des fichiers.

Il existe également des typedefs qui fournissent des spécialisations de `basic_fstream` propres aux caractères. Ils sont `fstream`, qui est un flux d’e/s de fichier qui est basé sur **char**, et `wfstream`, qui est un flux d’e/s de fichier qui est basé sur **wchar_t**. Pour plus d’informations, consultez [basic_fstream, classe](../standard-library/basic-fstream-class.md), [fstream](../standard-library/basic-fstream-class.md) et [wfstream](../standard-library/basic-fstream-class.md). L’utilisation de ces typedefs nécessite l’inclusion du fichier d’en-tête \<fstream>.

> [!NOTE]
> Quand un objet `basic_fstream` est utilisé pour effectuer des E/S de fichiers, bien que la mémoire tampon sous-jacente contienne des positions distinctes désignées pour la lecture et l’écriture, les positions actuelles d’entrée et de sortie sont liées. Ainsi, la lecture de certaines données déplace la position de sortie.

Le modèle de classe `basic_stringstream` et sa spécialisation courante, `stringstream`, sont souvent utilisés pour travailler avec des objets de flux d’E/S pour insérer et extraire des données de type caractère. Pour plus d’informations, consultez [basic_stringstream, classe](../standard-library/basic-stringstream-class.md).

## <a name="see-also"></a>Voir aussi

[stringstream](../standard-library/basic-stringstream-class.md)<br/>
[basic_stringstream, classe](../standard-library/basic-stringstream-class.md)<br/>
[\<sstream>](../standard-library/sstream.md)<br/>
[iostream, programmation](../standard-library/iostream-programming.md)<br/>
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)<br/>
