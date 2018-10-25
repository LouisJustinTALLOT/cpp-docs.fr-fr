---
title: Mots clés C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 80c1f0d4ac5d843732771281202612e31a4073c2
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860886"
---
# <a name="c-keywords"></a>Mots clés C

Les « mots clés » sont des mots qui ont une signification spéciale pour le compilateur C. Dans les phases de traduction 7 et 8, un identificateur ne peut pas avoir la même orthographe et la même casse qu'un mot clé C. Consultez une description des [phases de traduction](../preprocessor/phases-of-translation.md) dans *Référence du préprocesseur* ; pour obtenir des informations sur les identificateurs, consultez [Identificateurs](../c-language/c-identifiers.md). Le langage C utilise les mots clés suivants :

|||||
|-|-|-|-|
|**auto**|**double**|**int**|**struct**|
|**break**|**else**|**long**|**switch**|
|**case**|**enum**|**register**|**typedef**|
|**char**|**extern**|**return**|**union**|
|**const**|**float**|**short**|**unsigned**|
|**continue**|**for**|**signed**|**void**|
|**default**|**goto**|**sizeof**|**volatile**|
|**do**|**if**|**static**|**while**|

Vous ne pouvez pas redéfinir les mots clés. Toutefois, vous pouvez spécifier du texte à substituer pour des mots clés avant la compilation, à l’aide des [directives de préprocesseur](../preprocessor/preprocessor-directives.md) C.

**Section spécifique à Microsoft**

La norme ANSI C permet de réserver les identificateurs avec deux traits de soulignement à gauche pour les implémentations du compilateur. Par conséquent, la convention Microsoft est de faire précéder les noms des mots clés spécifiques à Microsoft de deux traits de soulignement. Ces mots ne peuvent pas être utilisés en tant que noms d'identificateurs. Pour obtenir une description des règles ANSI d’attribution de noms aux identificateurs, y compris l’utilisation de deux traits de soulignement, consultez [Identificateurs](../c-language/c-identifiers.md).

Les mots clés et les identificateurs spéciaux ci-dessous sont reconnus par le compilateur Microsoft C :

|||||
|-|-|-|-|
|**__asm**|**dllimport**<sup>2</sup>|**__int8**|**naked**<sup>2</sup>|
|**__based**<sup>1</sup>|**__except**|**__int16**|**__stdcall**|
|**__cdecl**|**__fastcall**|**__int32**|**thread**<sup>2</sup>|
|**__declspec**|**__finally**|**__int64**|**__try**|
|**dllexport**<sup>2</sup>|**__inline**|**__leave**||

<sup>1</sup> Le mot clé **__based** a des utilisations limitées pour les compilations 32 bits et 64 bits cibles.

<sup>2</sup> Ce sont des identificateurs spéciaux quand ils sont utilisés avec **__declspec** ; leur utilisation dans d’autres contextes n’est pas limitée.

Les extensions Microsoft sont activées par défaut. Pour garantir la portabilité totale de vos programmes, vous pouvez désactiver les extensions Microsoft en spécifiant l'option /Za (compilation pour compatibilité ANSI) pendant la compilation. Dans ce cas, les mots clés spécifiques à Microsoft sont désactivés.

Lorsque les extensions Microsoft sont activées, vous pouvez utiliser les mots clés répertoriés ci-dessus dans vos programmes. Pour la compatibilité ANSI, la plupart de ces mots clés sont précédés de deux traits de soulignement. Les quatre exceptions, **dllexport**, **dllimport**, **naked** et **thread**, sont utilisées uniquement avec **__declspec** et ne requièrent donc pas un double trait de soulignement à gauche. Pour assurer la compatibilité descendante, des versions à un seul trait de soulignement sont prises en charge pour les autres mots clés.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Éléments de C](../c-language/elements-of-c.md)
