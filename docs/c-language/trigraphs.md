---
title: Trigraphes
ms.date: 11/04/2016
helpviewer_keywords:
- ??) trigraph
- ??- trigraph
- question mark, in trigraphs
- ??= trigraph
- ?? trigraph
- ??< trigraph
- ??/ trigraph
- trigraphs
- '? symbol, trigraph'
- ??> trigraph
- ??! trigraph
- ??' trigraph
ms.assetid: 617f76ec-b8e8-4cfe-916c-4bc32cbd9aeb
ms.openlocfilehash: 001eb90b5cb4dda933571fd053598995d3ef613e
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152298"
---
# <a name="trigraphs"></a>Trigraphes

Le jeu de caractères source des programmes sources C est contenu dans le jeu de caractères ASCII de 7 bits, mais c'est un sur-ensemble de l'ensemble de code invariant ISO 646-1983. Les séquences de trigraphe permettent d'écrire des programmes C en utilisant uniquement l'ensemble de codes invariant ISO (organisation internationale de normalisation). Les trigraphes sont des séquences de trois caractères (introduites par deux points d'interrogation consécutifs) que le compilateur remplace par leurs caractères de ponctuation correspondants. Vous pouvez utiliser des trigraphes dans les fichiers sources C avec un jeu de caractères qui ne contient pas de représentation graphique pour certains caractères de ponctuation.

C++17 supprime les trigraphes du langage. Bien que cela soit déconseillé, les implémentations peuvent continuer à prendre en charge des trigraphes dans le cadre du mappage défini par l’implémentation entre le fichier source physique et le *jeu de caractères source de base*. Jusqu’à C++14, les trigraphes sont pris en charge comme dans C.

Visual C++ prend toujours en charge la substitution de trigraphes, mais celle-ci est désactivée par défaut. Pour plus d’informations sur la façon d’activer la substitution de trigraphes, consultez [/Zc:trigraphs (substitution de trigraphes)](../build/reference/zc-trigraphs-trigraphs-substitution.md).

Le tableau suivant indique les neuf séquences de trigraphe. Dans un fichier source, toutes les occurrences des caractères de ponctuation de la première colonne sont remplacées par le caractère correspondant de la deuxième colonne.

### <a name="trigraph-sequences"></a>Séquences de trigraphe

| Trigraphe | Caractère de ponctuation |
|----------|-----------------------|
| ??= | # |
| ??( | \[ |
| ??/ | \\ |
| ??) | ] |
| ??' | ^ |
| ??\< | { |
| ??! | &#124; |
| ??> | } |
| ??- | ~ |

Un trigraphe est toujours traité comme un caractère source unique. La traduction des trigraphes a lieu dans la première [phase de traduction](../preprocessor/phases-of-translation.md), avant la reconnaissance des caractères d’échappement dans les littéraux de chaîne et des constantes de caractère. Seuls les neuf trigraphes indiqués dans le tableau ci-dessus sont identifiés. Toutes les autres séquences de caractères restent inchangées.

La séquence d’échappement de caractère, **\\?**, évite que les séquences de caractères qui s’apparentent à un trigraphe ne soient mal interprétées. (Pour plus d’informations sur les séquences d’échappement, consultez [Séquences d’échappement](../c-language/escape-sequences.md).) Par exemple, si vous essayez d'imprimer la chaîne `What??!` avec cette instruction `printf`

```C
printf( "What??!\n" );
```

la chaîne imprimée est `What|`, car `??!` est une séquence de trigraphe qui est remplacée par le caractère `|`. Entrez l'instruction comme suit pour imprimer correctement la chaîne :

```C
printf( "What?\?!\n" );
```

Dans cette instruction `printf`, un caractère d'échappement barre oblique inverse devant le deuxième point d'interrogation empêche d'interpréter `??!` comme un trigraphe, ce qui serait une mauvaise interprétation.

## <a name="see-also"></a>Voir aussi

[/Zc:trigraphs (Substitution de trigraphes)](../build/reference/zc-trigraphs-trigraphs-substitution.md)<br/>
[identificateurs C](../c-language/c-identifiers.md)
