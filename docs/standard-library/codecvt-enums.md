---
description: 'En savoir plus sur les éléments suivants : &lt; &gt; énumérations codecvt'
title: '&lt;codecvt&gt;, énumérations'
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: bcd40f72f563b3ecf91125f7167f206d4b1b6517
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234057"
---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt&gt;, énumérations

## <a name="codecvt_mode-enumeration"></a><a name="codecvt_mode"></a> Énumération codecvt_mode

Spécifie des informations de configuration pour les facettes de [paramètres régionaux](../standard-library/locale-class.md) .

```cpp
enum codecvt_mode {
    consume_header = 4,
    generate_header = 2,
    little_endian = 1
};
```

### <a name="remarks"></a>Notes

L’énumération définit trois constantes qui fournissent des informations de configuration aux facettes de paramètres régionaux déclarées dans [\<codecvt>](../standard-library/codecvt.md) . Les différentes valeurs sont :

- `consume_header`, pour consommer une séquence d’en-têtes initiale pendant la lecture d’une séquence multioctet et déterminer le mode Endian de la séquence multioctet suivante à lire

- `generate_header`, pour générer une séquence d’en-têtes pendant l’écriture d’une séquence multioctet afin d’annoncer le mode Endian de la séquence multioctet suivante à écrire

- `little_endian`, pour générer une séquence multioctet dans l’ordre du plus petit endian, par opposition à l’ordre par défaut du plus grand endian

Ces constantes peuvent être liées par une condition OR dans des combinaisons arbitraires.

## <a name="see-also"></a>Voir aussi

[\<codecvt>](../standard-library/codecvt.md)
