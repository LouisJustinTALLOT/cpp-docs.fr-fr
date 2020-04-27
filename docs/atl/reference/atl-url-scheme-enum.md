---
title: ATL_URL_SCHEME, énumération
ms.date: 11/04/2016
helpviewer_keywords:
- ATLUTIL/ATL::ATL_URL_SCHEME
ms.assetid: f4131046-8ba0-4ec1-8209-84203f05d20e
ms.openlocfilehash: 6d8307d6ea51c5ec7e63735360b8628a4c1ed782
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168577"
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
