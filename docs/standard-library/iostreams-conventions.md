---
title: iostreams, conventions | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- iostream header
- C++ Standard Library, iostreams
ms.assetid: 9fe5ded0-37a1-48d1-9671-c81ffc4760ad
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37ba52981f317ff9929a820c42d35cde0506256f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846452"
---
# <a name="iostreams-conventions"></a>iostreams, conventions

Les en-têtes iostreams prennent en charge les conversions entre le texte et les formes codées, ainsi que l’entrée et la sortie vers des fichiers externes :

|||
|-|-|
|[\<fstream>](../standard-library/fstream.md)|[\<iomanip>](../standard-library/iomanip.md)|
|[\<ios>](../standard-library/ios.md)|[\<iosfwd>](../standard-library/iosfwd.md)|
|[\<iostream>](../standard-library/iostream.md)|[\<istream>](../standard-library/istream.md)|
|[\<ostream>](../standard-library/ostream.md)|[\<sstream>](../standard-library/sstream.md)|
|[\<streambuf>](../standard-library/streambuf.md)|[\<strstream>](../standard-library/strstream.md)|

L’utilisation la plus simple d’iostreams nécessite uniquement d’inclure l’en-tête [\<iostream>](../standard-library/iostream.md). Vous pouvez ensuite extraire des valeurs de [cin](../standard-library/iostream.md#cin) ou [wcin](../standard-library/iostream.md#wcin) pour lire l’entrée standard. Les règles sont présentées dans la description de la classe [basic_istream](../standard-library/basic-istream-class.md). Vous pouvez également insérer des valeurs dans [cout](../standard-library/iostream.md#cout) ou [wcout](../standard-library/iostream.md#wcout) pour écrire la sortie standard. Les règles sont présentées dans la description de la classe [basic_ostream](../standard-library/basic-ostream-class.md). Le contrôle de format commun aux extracteurs et aux inséreurs est géré par la classe [basic_ios](../standard-library/basic-ios-class.md). La manipulation de ces informations de format par l’extraction et l’insertion d’objets est gérée par plusieurs manipulateurs.

Vous pouvez effectuer les mêmes opérations iostreams sur des fichiers que vous ouvrez par nom, en utilisant les classes déclarées dans [\<fstream>](../standard-library/fstream.md). Pour effectuer une conversion entre des iostreams et des objets de la classe [basic_string](../standard-library/basic-string-class.md), utilisez les classes déclarées dans [\<sstream>](../standard-library/sstream.md). Pour faire de même avec des chaînes C, utilisez les classes déclarées dans [\<strstream>](../standard-library/strstream.md).

Les en-têtes restants fournissent des services de prise en charge, qui n’intéresseront généralement directement que les utilisateurs plus expérimentés des classes iostreams.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)<br/>
[iostream, programmation](../standard-library/iostream-programming.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
