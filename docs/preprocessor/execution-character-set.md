---
title: execution_character_set
ms.date: 10/18/2018
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
helpviewer_keywords:
- pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
ms.openlocfilehash: bd31e8e91a1bcbfa6ace9b47fa2b13dd945adb20
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039924"
---
# <a name="executioncharacterset"></a>execution_character_set

Spécifie le jeu de caractères d’exécution utilisé pour les littéraux de chaîne et de caractère. Cette directive n’est pas nécessaire pour les littéraux marquées avec le préfixe u8.

## <a name="syntax"></a>Syntaxe

```
#pragma execution_character_set("target")
```

### <a name="parameters"></a>Paramètres

*target*<br/>
Spécifie le jeu de caractères cible d’exécution. Actuellement, l’exécution de la cible uniquement définie pris en charge est « utf-8 ».

## <a name="remarks"></a>Notes

Cette directive de compilateur est obsolète à partir de Visual Studio 2015 Update 2. Nous vous recommandons d’utiliser le `/execution-charset:utf-8` ou `/utf-8` options du compilateur ainsi que d’à l’aide de la `u8` préfixe sur les littéraux de caractère et de chaîne étroits qui contiennent des caractères étendus. Pour plus d’informations sur la `u8` de préfixe, consultez [String and Character Literals](../cpp/string-and-character-literals-cpp.md). Pour plus d’informations sur les options du compilateur, consultez [/Execution-CharSet (définir l’exécution du jeu de caractères)](../build/reference/execution-charset-set-execution-character-set.md) et [/UTF-8 (définir la Source et exécutable jeux au format UTF-8 de caractères)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md).

Le `#pragma execution_character_set("utf-8")` directive indique au compilateur pour encoder les caractères étroits et les littéraux de chaîne étroits dans votre code source au format UTF-8 dans le fichier exécutable. Cet encodage de sortie est indépendant de l’encodage du fichier source utilisé.

Par défaut, le compilateur encode les chaînes étroites et les caractères étroits à l’aide de la page de codes actuelle en tant que le jeu de caractères d’exécution. Cela signifie que les caractères Unicode ou DBCS dans un littéral situés en dehors de la plage de la page de codes actuelle sont convertis en caractère de remplacement par défaut dans la sortie. Les caractères Unicode et DBCS sont tronquées à leurs octets de poids faible. Il s’agit certainement pas à vos attentes. Vous pouvez spécifier l’encodage UTF-8 pour les littéraux dans le fichier source en utilisant un `u8` préfixe. Le compilateur passe ces chaînes encodées UTF-8 à la sortie inchangée. Littéraux de caractère étroit préfixés à l’aide d’u8 doivent tenir dans un seul octet, ou elles sont tronquées lors de la sortie.

Par défaut, Visual Studio utilise la page de codes actuelle en tant que le jeu de caractères source utilisé pour interpréter votre code source pour la sortie. Lorsqu’un fichier est lu, Visual Studio l’interprète en fonction de la page de codes actuelle, sauf si la page de codes du fichier a été définie, ou, sauf si une marque d’ordre d’octet (BOM) ou de caractères UTF-16 sont détectées au début du fichier. UTF-8 ne peuvent pas être définis en tant que la page de codes actuelle, lorsque la détection automatique rencontre des fichiers sources codés en UTF-8 sans une nomenclature, Visual Studio part du principe qu’ils sont encodés à l’aide de la page de codes actuelle. Caractères dans le fichier source qui sont en dehors de la plage spécifié ou automatiquement détectées page de codes peut entraîner des erreurs et avertissements du compilateur.

## <a name="see-also"></a>Voir aussi

[Directives pragma et \_ \_mot clé (pragma)](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[/ EXECUTION-CharSet (définir l’exécution du jeu de caractères)](../build/reference/execution-charset-set-execution-character-set.md)<br/>
[/ UTF-8 (définir la Source et le fichier exécutable jeux de caractères UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)