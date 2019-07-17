---
title: bad_optional_access, classe
ms.date: 11/04/2016
f1_keywords:
- optional/std::bad_optional_access
ms.assetid: 89a3b805-ab60-4858-b772-5855130c11b1
ms.openlocfilehash: f898d1e30dd173339192bdb3b75581d12b62fca7
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269141"
---
# <a name="badoptionalaccess-class"></a>bad_optional_access, classe

Définit le type des objets levés comme exceptions pour signaler la situation où une tentative est effectuée pour accéder à la valeur d’un `optional` objet qui ne contient pas une valeur.

## <a name="syntax"></a>Syntaxe

```cpp
class bad_optional_access : public exception
{
    public: bad_optional_access();
};
```
