---
title: '&lt;codecvt&gt;, énumérations'
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: e67290d8de0b8251191c4a93b66b7e19a293ed61
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371942"
---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt&gt;, énumérations

## <a name="codecvt_mode-enumeration"></a><a name="codecvt_mode"></a>codecvt_mode Énumération

Spécifie les informations de configuration pour les facettes [locales.](../standard-library/locale-class.md)

```cpp
enum codecvt_mode {
    consume_header = 4,
    generate_header = 2,
    little_endian = 1
};
```

### <a name="remarks"></a>Notes

L’énumération définit trois constantes qui fournissent des informations de configuration aux facettes locales déclarées dans [ \<le codecvt>](../standard-library/codecvt.md). Les différentes valeurs sont :

- `consume_header`, pour consommer une séquence d’en-têtes initiale pendant la lecture d’une séquence multioctet et déterminer le mode Endian de la séquence multioctet suivante à lire

- `generate_header`, pour générer une séquence d’en-têtes pendant l’écriture d’une séquence multioctet afin d’annoncer le mode Endian de la séquence multioctet suivante à écrire

- `little_endian`, pour générer une séquence multioctet dans l’ordre du plus petit endian, par opposition à l’ordre par défaut du plus grand endian

Ces constantes peuvent être liées par une condition OR dans des combinaisons arbitraires.

## <a name="see-also"></a>Voir aussi

[\<codecvt>](../standard-library/codecvt.md)
