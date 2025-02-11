---
title: AEM Forms Data Integration
seo-title: AEM Forms Data Integration
description: Data Integration lets you integrate AEM Forms with disparate data sources and create form data model to create and work with adaptive forms and interactive communications.
seo-description: Data Integration lets you integrate AEM Forms with disparate data sources and create form data model to create and work with adaptive forms and interactive communications.
uuid: 58f65ae0-cf54-4249-92c7-64b557e30491
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integration
discoiquuid: b6786321-6e8e-40e2-809b-d117991246c4
feature: Form Data Model
exl-id: 8cbd3fb0-3c87-433e-bfd7-0f93216a5de7
---
# Introduction to AEM Forms Data Integration {#aem-forms-data-integration}

Data Integration lets you integrate AEM Forms with disparate data sources and create form data model to create and work with adaptive forms and interactive communications.

 ![](do-not-localize/data-integeration.png)

Enterprise infrastructures include disparate back-end systems or data sources like databases, web services, REST services, OData services, and CRM solutions. Put together, they make an information system that serves data to enterprise applications to perform day-to-day business. On the other hand, applications capture data and send it back to update data sources.

AEM Forms applications like adaptive forms and interactive communications require integration with data sources to fetch customer data while rendering forms and creating interactive communications. There are use cases when data is fetched from data sources based on user inputs in adaptive forms. In addition, the submitted adaptive form data can be written back to update the respective data sources.

While a distributed, modular system has its own benefits, the challenge lies in integrating and creating data associations across data sources. Data integration is the key to a functional and efficient enterprise infrastructure with disparate data sources connected to applications for exchange of business data.

## Data Integration overview {#data-integration-overview}

![aem-forms-data-integeration](assets/aem-forms-data-integeration.png)

AEM Forms Data Integration allows configuring and connecting disparate data sources with AEM Forms. It provides an intuitive user interface to create a unified data representation schema of business entities and services across connected data sources. The unified representation is known as a form data model, an extension of JSON schema. The entities in a form data model are referred to as data model objects. A form data model allows you to:

* Access data model objects, properties, and services from connected data sources.
* Create custom data model objects and properties
* Build associations between data model objects within and across data sources.
* Invoke data model object services to query or write data to and from data sources.

Once you have created a form data model, you can use it in various adaptive form and interactive communications workflows, such as:

* Create adaptive forms and interactive communications based on form data model
* Prefill adaptive forms and interactive communications from configured data sources
* Invoke data source services/operations using adaptive form rules
* Write submitted adaptive form data to data sources

## Get started with data integration {#get-started-with-data-integration}

The first step to implement data integration is to identify and configure data sources that store information you want to leverage in adaptive forms and interactive communications use cases. Next, you create a form data model that uses data model object, properties, and services from one or more data sources. You can create adaptive forms and interactive communications based on a form data model where adaptive form fields or placeholders in interactive communications are bound to respective data source properties.

AEM Forms also allows you to create a form data model independent of data sources and associate or bind data model objects and properties in the form data model with data source later. It eliminates any dependencies on data sources while you work on a form data model.

Review the following to get started, understand, and implement data integration.

* [Configure data sources](/help/forms/using/configure-data-sources.md)
* [Create form data model](/help/forms/using/create-form-data-models.md)
* [Work with form data model](/help/forms/using/work-with-form-data-model.md)
* [Use form data model](/help/forms/using/using-form-data-model.md)
