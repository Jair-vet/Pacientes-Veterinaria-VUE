<script scope>

</script>


<template>
    <div className="md:w-1/2 lg:w-2/5 mb-8">
        <h2 className="font-black text-3xl text-center">Seguimiento Pacientes</h2>

        <p className="mt-5 text-center text-lg font-bold mb-2">Añade Pacientes y 
            <span className="text-sky-500 font-bold">Administralos</span>
        </p>

        <form className="bg-gray-50 shadow-md rounded-lg py-10 px-5 md:m-0 m-4">
            
            <div className="mb-5">
                <label htmlFor="mascota" className="block text-gray-700 uppercase font-bold">
                    Nombre Mascota
                </label>
                <input 
                    id="mascota"
                    type="text"
                    placeholder="Nombre de la Mascota"
                    className="border w-full rounded-md p-2 mt-2 focus:outline-none focus:ring
                        focus:ring-sky-500 hover:"
                    name="mascota"
                />
            </div>
            
            <div className="mb-5">
                <label htmlFor="propietario" className="block text-gray-700 uppercase font-bold">
                    Nombre Propietario
                </label>
                <input 
                    id="propietario"
                    type="text"
                    placeholder="Nombre del Propetario"
                    className="border w-full rounded-md p-2 mt-2 focus:outline-none focus:ring
                        focus:ring-sky-500 "
                    name="propietario"
                />
            </div>
            
            <div className="mb-5">
                <label htmlFor="email" className="block text-gray-700 uppercase font-bold">
                    Email
                </label>
                <input 
                    id="email"
                    type="email"
                    placeholder="Email para Contactar"
                    className="border w-full rounded-md p-2 mt-2 focus:outline-none focus:ring
                        focus:ring-sky-500 "
                    name="email"
                />
            </div>
            
            <div className="mb-5">
                <label htmlFor="alta" className="block text-gray-700 uppercase font-bold">
                    Día de Ingreso
                </label>
                <input 
                    id="alta"
                    type="date"
                    className="border w-full rounded-md p-2 mt-2 focus:outline-none focus:ring
                        focus:ring-sky-500 "
                    name="alta"
                />
            </div>
            
            <div className="mb-5">
                <label htmlFor="sintomas" className="block text-gray-700 uppercase font-bold">
                    Síntomas
                </label>
                <textarea 
                    id="sintomas"
                    placeholder="Describe los Sintomas"
                    className="border w-full rounded-md p-2 mt-2 focus:outline-none focus:ring
                        focus:ring-sky-500 "
                    name="sintomas"
                />
            </div>

            <input 
                type="submit"
                className="bg-sky-500 w-full rounded-md p-3 text-white uppercase font-bold
                            hover:bg-sky-700 cursor-pointer transition-colors" 
            />

        </form>
    </div>
</template>
