---
description: 'En savoir plus sur : pragma execution_character_set'
title: execution_character_set, pragma
ms.date: 08/29/2019
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
helpviewer_keywords:
- pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
ms.openlocfilehash: 057013e669d7c6a4b31c02fe9c6319ea05eb7780
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300479"
---
# <a name="execution_character_set-pragma"></a>execution_character_set, pragma

Spécifie le jeu de caractères d’exécution utilisé pour les littéraux de chaîne et de caractère. Cette directive n’est pas nécessaire pour les littéraux marqués avec le `u8` préfixe.

## <a name="syntax"></a>Syntaxe

> **execution_character_set #pragma (** "*cible*" **)**

### <a name="parameters"></a>Paramètres

*Indicatif*\
Spécifie le jeu de caractères d’exécution cible. Actuellement, le seul jeu d’exécution cible pris en charge est « UTF-8 ».

## <a name="remarks"></a>Notes

Cette directive du compilateur est obsolète à compter de Visual Studio 2015 Update 2. Nous vous recommandons d’utiliser les `/execution-charset:utf-8` `/utf-8` Options du compilateur ou en utilisant le `u8` préfixe sur des caractères étroits et des littéraux de chaîne qui contiennent des caractères étendus. Pour plus d’informations sur le `u8` préfixe, consultez [littéraux de chaîne et de caractère](../cpp/string-and-character-literals-cpp.md). Pour plus d’informations sur les options du compilateur, consultez [/Execution-charset (définir le jeu de caractères d’exécution)](../build/reference/execution-charset-set-execution-character-set.md) et [/UTF-8 (définir les jeux de caractères source et exécutable sur UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md).

La `#pragma execution_character_set("utf-8")` directive indique au compilateur d’encoder des littéraux de chaîne étroits et étroits dans votre code source au format UTF-8 dans l’exécutable. Cet encodage de sortie est indépendant de l’encodage du fichier source utilisé.

Par défaut, le compilateur encode les caractères étroits et les chaînes étroites en utilisant la page de codes actuelle comme jeu de caractères d’exécution. Cela signifie que les caractères Unicode ou DBCS dans un littéral qui se trouvent en dehors de la plage de la page de codes actuelle sont convertis en caractère de remplacement par défaut dans la sortie. Les caractères Unicode et DBCS sont tronqués à leur octet de poids faible. C’est presque certainement pas ce que vous envisagez. Vous pouvez spécifier l’encodage UTF-8 pour les littéraux dans le fichier source à l’aide d’un `u8` préfixe. Le compilateur passe ces chaînes encodées en UTF-8 à la sortie inchangée. Les littéraux de caractère étroit préfixés à l’aide de U8 doivent tenir dans un octet, ou ils sont tronqués à la sortie.

Par défaut, Visual Studio utilise la page de codes actuelle comme jeu de caractères source utilisé pour interpréter votre code source pour la sortie. Lorsqu’un fichier est lu dans, Visual Studio l’interprète en fonction de la page de codes en cours, sauf si la page de codes du fichier a été définie, ou à moins qu’une marque d’ordre d’octet (BOM) ou des caractères UTF-16 ne soit détectée au début du fichier. Étant donné qu’UTF-8 ne peut pas être défini comme page de codes actuelle, lorsque la détection automatique rencontre des fichiers sources encodés au format UTF-8 sans BOM, Visual Studio suppose qu’ils sont encodés à l’aide de la page de codes actuelle. Les caractères du fichier source qui se trouvent en dehors de la plage de la page de codes spécifiée ou détectée automatiquement peuvent provoquer des avertissements et des erreurs du compilateur.

## <a name="see-also"></a>Voir aussi

[Directives pragma et \_ \_ mot clé pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[/Execution-charset (définir le jeu de caractères d’exécution)](../build/reference/execution-charset-set-execution-character-set.md)\
[/UTF-8 (définir les jeux de caractères source et exécutable sur UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)
