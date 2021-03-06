---
description: En savoir plus sur les spécifications de caractères octaux et hexadécimaux
title: Spécifications de caractères octaux et hexadécimaux
ms.date: 11/04/2016
helpviewer_keywords:
- octal characters
- hexadecimal characters
ms.assetid: 9264f3ec-46b8-41a5-b21a-8f7ed0a11871
ms.openlocfilehash: 91646244a30cb3ec5ad965914f1bee855fba05d7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243274"
---
# <a name="octal-and-hexadecimal-character-specifications"></a>Spécifications de caractères octaux et hexadécimaux

La séquence **\\** <em>OOO</em> signifie que vous pouvez spécifier n’importe quel caractère dans le jeu de caractères ASCII comme code de caractère octal à trois chiffres. La valeur numérique de l'entier octal spécifie la valeur du caractère ou du caractère élargi souhaité.

De même, la séquence **\x**<em>hhh</em> vous permet de spécifier tout caractère ASCII comme code de caractère hexadécimal. Par exemple, vous pouvez donner le caractère de retour arrière ASCII comme séquence d'échappement C normale (**\b**), ou vous pouvez le coder comme **\010** (octal) ou **\x008** (hexadécimal).

Vous pouvez utiliser uniquement des chiffres de 0 à 7 dans une séquence d'échappement octale. Les séquences d'échappement octales ne peuvent jamais être plus longues que trois chiffres et elles se terminent par le premier caractère qui n'est pas un chiffre octal. Bien que vous n'ayez pas besoin d'utiliser les trois chiffres, vous devez en utiliser au moins un. Par exemple, la représentation octale est **\10** pour le caractère de retour arrière ASCII et **\101** pour la lettre A, comme spécifié dans un graphique ASCII.

De même, vous devez utiliser au moins un chiffre pour une séquence d'échappement hexadécimale, mais vous pouvez omettre le deuxième et le troisième chiffre. Par conséquent vous pouvez spécifier la séquence d'échappement hexadécimale pour le caractère de retour arrière comme **\x8**, **\x08** ou **\x008**.

La valeur de la séquence d’échappement octale ou hexadécimale doit se trouver dans la plage de valeurs représentables pour le type **`unsigned char`** pour une constante de caractère et **`wchar_t`** un type pour une constante à caractères larges. Consultez [Caractères multioctets et larges](../c-language/multibyte-and-wide-characters.md) pour obtenir des informations sur les constantes à caractères larges.

Contrairement aux constantes octales d'échappement, le nombre de chiffres hexadécimaux d'une séquence d'échappement est illimité. Une séquence d'échappement hexadécimale se termine au premier caractère qui n'est pas un chiffre hexadécimal. Les chiffres hexadécimaux incluant les lettres **a** à **f**, vous devez vous assurer que la séquence d'échappement se termine au chiffre prévu. Pour éviter toute confusion, vous pouvez placer des définitions octales ou hexadécimales de caractère dans une définition de macro :

```
#define Bell '\x07'
```

Pour les valeurs hexadécimales, vous pouvez désactiver la chaîne pour montrer la valeur correcte clairement :

```
"\xabc"    /* one character  */
"\xab" "c" /* two characters */
```

## <a name="see-also"></a>Voir aussi

[Constantes caractère C](../c-language/c-character-constants.md)
