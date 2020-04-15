---
title: TemplateInstantiation classe
description: La référence de classe de conception de CMD Build Insights SDK TemplateInstantiation.
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiation
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ba8fd10efc6a536c9160f10b19e19e17bfaaad98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324219"
---
# <a name="templateinstantiation-class"></a>TemplateInstantiation classe

::: moniker range="<=vs-2015"

Le SDK Build Insights est compatible avec Visual Studio 2017 et plus. Pour voir la documentation de ces versions, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2017 ou Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range=">=vs-2017"

La `TemplateInstantiation` classe est utilisée avec les fonctions [MatchEvent](../functions/match-event.md), [MatchEventInMemberFunction](../functions/match-event-in-member-function.md), [MatchEventStack](../functions/match-event-stack.md)et [MatchEventStackInMemberFunction.](../functions/match-event-stack-in-member-function.md) Utilisez-le pour correspondre à un [événement TEMPLATE_INSTANTIATION.](../event-table.md#template-instantiation)

## <a name="syntax"></a>Syntaxe

```cpp
class TemplateInstantiation : public Activity
{
public:
    enum class Kind
    {
        CLASS       = TEMPLATE_INSTANTIATION_KIND_CODE_CLASS,
        FUNCTION    = TEMPLATE_INSTANTIATION_KIND_CODE_FUNCTION,
        VARIABLE    = TEMPLATE_INSTANTIATION_KIND_CODE_VARIABLE,
        CONCEPT     = TEMPLATE_INSTANTIATION_KIND_CODE_CONCEPT
    };

    TemplateInstantiation(const RawEvent& event);

    const unsigned long long& SpecializationSymbolKey() const;
    const unsigned long long& PrimaryTemplateSymbolKey() const;

    Kind Kind() const;
};
```

## <a name="members"></a>Membres

Avec les membres hérités de sa `TemplateInstantiation` classe de base [d’activité,](activity.md) la classe contient les membres suivants :

### <a name="constructors"></a>Constructeurs

[TemplateInstantiation](#template-instantiation)

### <a name="functions"></a>Fonctions

[Kind](#kind)
[PrimaryTemplateSymbolKey](#primary-template-symbol-key)
[SpecializationSymbolKey](#specialization-symbol-key)

## <a name="kind"></a><a name="kind"></a>Genre

```cpp
Kind Kind() const;
```

### <a name="return-value"></a>Valeur de retour

Un code décrivant le type d’instantanéisation du modèle qui a été fait.

## <a name="primarytemplatesymbolkey"></a><a name="primary-template-symbol-key"></a>PrimaryTemplateSymbolKey

```cpp
const unsigned long long& PrimaryTemplateSymbolKey() const;
```

### <a name="return-value"></a>Valeur de retour

Un identifiant numérique pour le type de modèle qui était spécialisé. Cet identifiant est unique dans un pass frontale compilateur.

## <a name="specializationsymbolkey"></a><a name="specialization-symbol-key"></a>SpécialisationSymbolKey

```cpp
const unsigned long long& SpecializationSymbolKey() const;
```

### <a name="return-value"></a>Valeur de retour

Un identifiant numérique pour le type de spécialisation. Cet identifiant est unique dans un pass frontale compilateur.

## <a name="templateinstantiation"></a><a name="template-instantiation"></a>TemplateInstantiation

```cpp
TemplateInstantiation(const RawEvent& event);
```

### <a name="parameters"></a>Paramètres

*Événement*\
Un [événement TEMPLATE_INSTANTIATION.](../event-table.md#template-instantiation)

::: moniker-end
