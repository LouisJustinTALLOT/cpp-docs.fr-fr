---
description: 'En savoir plus sur : ATL_URL_SCHEME'
title: ATL_URL_SCHEME, énumération
ms.date: 11/04/2016
helpviewer_keywords:
- ATLUTIL/ATL::ATL_URL_SCHEME
ms.assetid: f4131046-8ba0-4ec1-8209-84203f05d20e
ms.openlocfilehash: 72c149345a0e1edd41bfc9b32d1e94ab6477d488
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165132"
---
# <a name="atl_url_scheme"></a>ATL_URL_SCHEME

Les membres de cette énumération fournissent des constantes pour les schémas comprises par la [boucle](curl-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
enum ATL_URL_SCHEME{
   ATL_URL_SCHEME_UNKNOWN = -1,
   ATL_URL_SCHEME_FTP     = 0,
   ATL_URL_SCHEME_GOPHER  = 1,
   ATL_URL_SCHEME_HTTP    = 2,
   ATL_URL_SCHEME_HTTPS   = 3,
   ATL_URL_SCHEME_FILE    = 4,
   ATL_URL_SCHEME_NEWS    = 5,
   ATL_URL_SCHEME_MAILTO  = 6,
   ATL_URL_SCHEME_SOCKS   = 7
};
```

## <a name="requirements"></a>Spécifications

**En-tête :** atlutil. h

## <a name="see-also"></a>Voir aussi

[Concepts](../active-template-library-atl-concepts.md)<br/>
[Boucle :: SetScheme](curl-class.md#setscheme)<br/>
[Boucle :: GetScheme](curl-class.md#getscheme)
