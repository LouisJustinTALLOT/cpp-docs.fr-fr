---
description: 'En savoir plus sur : conventions iostreams'
title: iostreams, conventions
ms.date: 11/04/2016
helpviewer_keywords:
- iostream header
- C++ Standard Library, iostreams
ms.assetid: 9fe5ded0-37a1-48d1-9671-c81ffc4760ad
ms.openlocfilehash: 3676c6aa14a5ebac1d39ed50821449caa7313e40
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231392"
---
# <a name="iostreams-conventions"></a>iostreams, conventions

Les en-têtes iostreams prennent en charge les conversions entre le texte et les formes codées, ainsi que l’entrée et la sortie vers des fichiers externes :

[\<fstream>](../standard-library/fstream.md)\
[\<iomanip>](../standard-library/iomanip.md)\
[\<ios>](../standard-library/ios.md)\
[\<iosfwd>](../standard-library/iosfwd.md)\
[\<iostream>](../standard-library/iostream.md)\
[\<istream>](../standard-library/istream.md)\
[\<ostream>](../standard-library/ostream.md)\
[\<sstream>](../standard-library/sstream.md)\
[\<streambuf>](../standard-library/streambuf.md)\
[\<strstream>](../standard-library/strstream.md)

L’utilisation la plus simple de iostreams nécessite uniquement que vous incluiez l’en-tête [\<iostream>](../standard-library/iostream.md) . Vous pouvez ensuite extraire des valeurs de [cin](../standard-library/iostream.md#cin) ou [wcin](../standard-library/iostream.md#wcin) pour lire l’entrée standard. Les règles sont présentées dans la description de la classe [basic_istream](../standard-library/basic-istream-class.md). Vous pouvez également insérer des valeurs dans [cout](../standard-library/iostream.md#cout) ou [wcout](../standard-library/iostream.md#wcout) pour écrire la sortie standard. Les règles sont présentées dans la description de la classe [basic_ostream](../standard-library/basic-ostream-class.md). Le contrôle de format commun aux extracteurs et aux inséreurs est géré par la classe [basic_ios](../standard-library/basic-ios-class.md). La manipulation de ces informations de format par l’extraction et l’insertion d’objets est gérée par plusieurs manipulateurs.

Vous pouvez effectuer les mêmes opérations iostreams sur les fichiers que vous ouvrez par nom, à l’aide des classes déclarées dans [\<fstream>](../standard-library/fstream.md) . Pour effectuer une conversion entre iostreams et des objets de classe [Basic_string classe](../standard-library/basic-string-class.md), utilisez les classes déclarées dans [\<sstream>](../standard-library/sstream.md) . Pour faire de même avec les chaînes C, utilisez les classes déclarées dans [\<strstream>](../standard-library/strstream.md) .

Les en-têtes restants fournissent des services de prise en charge, qui n’intéresseront généralement directement que les utilisateurs plus expérimentés des classes iostreams.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
