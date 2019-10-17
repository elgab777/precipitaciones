# precipitaciones

















import xlrd
from arrays import Array3D

def main():
    a3 = Array3D(34.32,14)
    for anio in range(1985,2019,1):
        ruta = './precipitacion /'+str(anio)+'precip.xlsx'
        archivo =xlrd.open_woekbook(filename=ruta)
        hoja = archivo.sheet_by_index(0)
        for r in range(1,33,1):
            for c in range(0,14,1):
                a3.set_item(anio-1985,r-1,c,hoja.cell_value( r , c ))
                
    estados= ["ENTIDAD","AGUASCALIENTES","BAJA CALIFORNIA","BAJA CALIFORNIA SUR","CAMPECHE","CAOHUILA","COLIMA","CHIAPAS","CHIHUAHUA","DISTRITO FEDERAL","DURANGO","GUANAJUATO","GUERRERO","HIDALGO","JALISCO","ESTADO DE MEXICO","MICHOACAN","MORELOS","NAYARIT","NUEVO LEON","OAXACA","PUEBLA","QUERETARO","QUINTANA ROO","SAN LUIS POTOSI","SINALOA","SONORA","TABASCO","TAMAULIPAS","TLAXCALA","VERACRUZ","YUCATAN","ZACATECAS","NACIONAL"]
    mes = ["MES","ENERO","FEBRERO","MARZO","ABRIL","MAYO","JUNIO","JULIO","AGOSTO","SEPTIEMPRE","OCTUBRE","NOVIEMBRE","DICIEMBRE"]

    print("+---------------------------+\n \t1")
    a= int(input("Año(1985-2019):"))
    e= int(input("Estado(1-32):"))
    m= int(input("Mes(1-12):"))
    x= a3.get_item(a-1985,e,m)


    print("\nEn el estado de " , estados[e],"llovio un promedio de",x,"centimetros cubicos en el " ,mes[m],"de",anio[a])
           )

    print("+---------------------------+\n \t2")
    sums = 0
    e2 = int(input("Estado(1-32):"))
    m2 = int(input("Mes(1-12):"))
    for g in range(1985,2019,1):
        a2 = a3.get_item(g-1985,e2,m2)
        sums = a2 + sums
    print("\n",estados[e2],"Promedio(1985-2018)","Mes de :",mes[m2],"\n")
    print(sums/(g-1985))
    print("\n+--------------------------+\n \t3")

    promTo = 0
    e3 = int(input("Estado (1-32):"))
    for z in range(0,12,1):
        z+=1
        for g in range(1985,2019,1):
            v2 = a3.get_item(g-1985,e3,z)
            promTo = v2 + promTo
    print("\n",estados[e3],"\n")
    print(promTo/(z*34))
    print("\n")

    promT = 0
    for r in range(0,32,1):
        r += 1
        for t in range(12,13,1):
            t += 1
            for g in range(1985,2019,1):
                s2 = a3.get_item(g-1985,r,t)
                promT = s2 + promT

    print("+-------------------------------+ \n \t4")
    print("El promedio general es : ",promT/(r*(g-1984)))
       

main()        
