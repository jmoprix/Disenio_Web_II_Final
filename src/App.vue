<template>

  <div class="flex flex-col h-screen">
    <navbar :menu_items=menu_data phone_number="+591 72677902" :company_name=company_name email="jmoprix@gmail.com" />


    <div class='flex-grow bg-white-300 dark:bg-gray-500'>

      <home v-if="current_option.state === 'inicio'" :data=home_data />

      <services v-if="current_option.state === 'servicios'" :data=development_data />



      <pricing v-if="current_option.state === 'precios'" :data=precios_data :activate=precios_menu />


      <about v-if="current_option.state === 'nosotros'" class="flex grow justify-center bg-white  w-full p-10"/>
        
      











    </div>



    <foot :company_name=company_name fb_link="https://www.facebook.com/jmoprix/" git_link="https://github.com/jmoprix/" />

  </div>
</template>









<script setup>

import { reactive } from 'vue'
import navbar from "./views/navbar.vue"
import foot from "./views/foot.vue"
import home from "./views/home.vue"
import services from './views/services.vue'
import pricing from "./views/pricing.vue"
import about from "./views/about.vue"



const company_name = "Jhonny Herrera Baldivieso - Developer"

let current_option = reactive({ state: 'inicio' })
let precios_menu = NaN


let home_data = {
  "desktop": {
    title: "¿Aplicación de escritorio dedicada para su negocio?",
    description: "Independiente o basado en la nube, podemos proporcionar una solución para nuestros clientes. Desarrollamos aplicaciones que no solo son multiplataforma sino también rentables. Tenemos experiencia en tecnologías como JavaFx, Dot Net, etc.",
  },
  "web_back": {
    title: "Solución de base de datos a prueba de futuro y escalable.",
    description: "La mayoría de los marcos de back-end relacionables, robustos y escalables son nuestra primera opción cuando planificamos soluciones. Tenemos años de experiencia en tecnologías probadas como Django, Laravel y Spring Boot."
  },
  "mobile": {
    title: "¿Quiere una aplicación de iOS y Android dedicada y personalizada?",
    description: "Brindamos servicios para construir aplicaciones de acuerdo a sus requerimientos. Creamos para iOS y Android ambos por el mismo costo. Confíe en nosotros para resolver sus problemas."
  },

}






let development_data = {

  heading: {
    title: 'Titulo',
    description: 'Descripción',

  },
  features: {
    seo: {
      title: "SEO (optimización de motores de búsqueda)",
      description: "Ofrecemos servicios de SEO para mejorar la visibilidad y el ranking del sitio web. Nuestro equipo utiliza las últimas técnicas para impulsar el tráfico orgánico. Los servicios incluyen investigación de palabras clave, optimización en la página, construcción de enlaces, optimización de contenido y SEO local. El objetivo es ofrecer resultados medibles y aumentar la presencia en línea de los clientes. "
    },
    repair: {
      title: "Mantenimiento / Actualización",
      description: "Nos especializamos en el mantenimiento, reparación, actualización y escalado de software para empresas. Nuestro equipo de expertos puede solucionar y resolver problemas de software rápidamente. Ofrecemos servicios de mantenimiento, reparación, actualización y escalado para garantizar que el software siempre funcione sin problemas y esté actualizado. "
    },
    web: {
      title: "Desarrollo web",
      description: "Ofrecemos desarrollo web utilizando Vue3, React, Django, PHP y Laravel para crear sitios web eficientes. Nuestra competencia en múltiples marcos nos permite satisfacer las diversas necesidades de los clientes con soluciones personalizadas. "
    },
    pbx: {
      title: "Telefonía IP",
      description: "Brindamos servicios de instalación y configuración de PBX (Private Branch Exchange) para empresas de todos los tamaños. Nuestros expertos tienen conocimiento y experiencia en configurar y configurar sistemas PBX para satisfacer las necesidades específicas de nuestros clientes. Ayudamos a las empresas a mejorar la eficiencia de sus comunicaciones y reducir costos. "
    }
    ,
    desktop:
    {
      title: "Aplicación de escritorio",
      description: "Nos especializamos en el desarrollo de software de escritorio robusto utilizando una variedad de tecnologías como JavaFX, Dot Net, Qt y más. Ya sea que su negocio esté relacionado con las finanzas, la atención médica o la logística, estamos bien preparados para brindarle las soluciones de software que necesita para ejecutar en dispositivos de escritorio. "
    },
    phone:
    {
      title: "Aplicación movil (iOS / Android)",
      description: "Nos especializamos en el desarrollo de aplicaciones móviles eficientes y de alto rendimiento para plataformas Android e iOS. Utilizando arquitectura web y tecnologías escalables, nuestro equipo de desarrolladores altamente calificados puede diseñar aplicaciones fáciles de usar que pueden acomodar una base de usuarios sustancial."
    }

  }
}

let menu_data = {
  "Inicio": current_option_initiate,
  "Servicios": current_option_initiate,
  "Nosotros": current_option_initiate,
  "Precios": {

    Desarrollo: precios_menu_initiate, // Name is very important, The name must match with other pricing menu options
    Seo: precios_menu_initiate,
    "Teléfono" : precios_menu_initiate

  },

}



let precios_data = {

  "desarrollo": [{
    title: "Desarrollo web",
    description: "Empezando desde",
    money: "$700",
    features: ["Arquitectura de página única/múltiple", "Backend escalable", "Hermosa UI/UX", "Personalizable"]

  },
  {
    title: "Aplicación movil",
    description: "Empezando desde",
    money: "$899",
    features: ["Tanto iOS como Android", "Seguridad avanzada", "IU optimizada", "Seguimiento de clientes", "Implementación gratuita en la tienda"]

  },
  {
    title: "Aplicación de escritorio",
    description: "Empezando desde",
    money: "$499",
    features: ["Nube/Base de datos local", "Compatibilidad cruzada (Linux/Windows)", "Optimizado", "Interfaz de usuario avanzada"]

  },
  ],

  "teléfono": [
    {
      description: "Optimización de motores de búsqueda para pequeñas empresas y personas que desean mejorar su clasificación y visibilidad en los motores de búsqueda.\nEl paquete generalmente incluye investigación de palabras clave, optimización en la página, construcción de enlaces, estrategias avanzadas como\nSEO local, SEO técnico y marketing de contenido, así como informes mensuales."
    }

  ], 

  "seo" : [
    {
      title: "PBX Básica (Única)" ,
      description: "Empezando desde",
      money: "$1000",
      features: ["On-premises", "Add-on options available", "Scalable to grow with business",]
    },
    {
      title: "PBX Avanzado (Única Vez)" ,
      description: "Empezando desde ",
      money: "$1500",
      features: ["Local", "Funciones avanzadas, como enrutamiento de llamadas y correo de voz", "Integración con CRM y otro software", "Integración con IA"]
    },
    {
      title: "Centralita Avanzada (Nube)",
      description: "Empezando desde (Mensual)",
      money: "$70",
      features: ["Nube","Integración con IA","Escalable para crecer con el negocio","Fácil de configurar y usar"]
    },
    {
      title: "PBX Básica (Única)" ,
      description: "Empezando desde ",
      money: "$1000",
      features: ["En las instalaciones", "Opciones adicionales disponibles", "Escalable para crecer con el negocio",]
    },
    {
      title: "Centralita Básica (Nube)",
      description: "Empezando desde (Mensual)",
      money: "$50",
      features: ["Nube", "Opciones adicionales disponibles", "Escalable para crecer con el negocio", "Fácil de configurar y usar"]
    },
  ]


}







function handel_menu_change(target) {
  current_option.state = 'none'
  setTimeout(() => current_option.state = target, 100)
}

function precios_menu_initiate(selected) {
  
  precios_menu = selected
  handel_menu_change('precios')
  // console.log(selected)
}

function current_option_initiate(current) {
  // handel_fade(current)
  handel_menu_change(current)
  
  
}
/// Fro pre loading images


let price_background_image = new Image()
price_background_image.src = '/contact.webp' 




</script>































<style scoped>


</style>