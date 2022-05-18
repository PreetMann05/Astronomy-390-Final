# Astronomy-390-Final
from numpy import *
import matplotlib.pyplot

x = []
y = []
days = []
velocity = []

days_mercury = 88
days_venus = 225
days_earth = 365
days_mars = 687
days_jupiter = 4332
days_saturn = 10760
days_uranus = 30684
days_neptune = 60188


def Sun():
    # draw sphere
    u, v = mgrid[0:2 * pi:50j, 0:pi:50j]
    sunx = cos(u) * sin(v) * 696.34
    suny = sin(u) * sin(v) * 696.34
    x.append(sunx), y.append(suny)


def Mercury_orbit():
    L = 9.11 * 10 ** 38  # L = angular momentum
    m = 3.28 * 10 ** 23  # m = mass of mercury
    M = 1.99 * 10 ** 30  # M = mass of sun
    a = 5.8 * 10 ** 10  # a = semi-major axis
    G = 6.674 * 10 ** -11  # G = Gravitational constant
    k = G * M * m
    E = -k / (2 * a)  # E = energy
    p = L ** 2 / (m * k)
    c = 1 + (2 * E * L ** 2) / (m * k ** 2)
    e = 0.2056  # e = eccentricity

    def fx(x):
        r = p / (1 + e * cos(x))
        return r

    phi = linspace(0, 2 * pi, days_mercury)
    merpythag = zeros([days_mercury])
    mervelocity = zeros([days_mercury])
    radius = zeros([days_mercury])
    theta = zeros([days_mercury])
    merx = zeros([days_mercury])
    mery = zeros([days_mercury])

    for i in range(0, days_mercury):
        radius[i] = fx(phi[i])
        theta[i] = 180 * phi[i] / pi
        mervelocity[i] = radius[i] * L
    

    for i in range(0, days_mercury):
        merx[i] = radius[i] * cos(phi[i]) / 10000000
        mery[i] = radius[i] * sin(phi[i]) / 10000000

    merdays = []
    for i in range(0, days_mercury):
        merdays.append(i+1)

    for i in range(1, days_mercury):
        mervelocity[0] = 0
        merpythag[i] = sqrt((merx[i]-merx[i-1])**2 + (mery[i]-mery[i-1])**2)
        mervelocity[i] = merpythag[i]

    x.append(merx), y.append(mery), velocity.append(mervelocity), days.append(merdays)

def Venus_orbit():
    L = 1.8 * 10 ** 40  # L = angular momentum
    m = 4.87 * 10 ** 24  # m = mass of venus
    M = 1.99 * 10 ** 30  # M = mass of sun
    a = 10.8 * 10 ** 10  # a = semi-major axis
    G = 6.674 * 10 ** -11  # G = Gravitational constant
    k = G * M * m
    E = -k / (2 * a)  # E = energy
    p = L ** 2 / (m * k)
    c = 1 + (2 * E * L ** 2) / (m * k ** 2)
    e = 0.007  # e = eccentricity

    def fx(x):
        r = p / (1 + e * cos(x))
        return r

    phi = linspace(0, 2 * pi, days_venus)
    venpythag = zeros([days_venus])
    venvelocity = zeros([days_venus])
    radius = zeros([days_venus])
    theta = zeros([days_venus])
    venx = zeros([days_venus])
    veny = zeros([days_venus])

    for i in range(0, days_venus):
        radius[i] = fx(phi[i])
        theta[i] = 180 * phi[i] / pi

    for i in range(0, days_venus):
        venx[i] = radius[i] * cos(phi[i]) / 10000000
        veny[i] = radius[i] * sin(phi[i]) / 10000000

    vendays = []
    for i in range(0, days_venus):
        vendays.append(i+1)

    for i in range(1, days_venus):
        venvelocity[0] = 0
        venpythag[i] = sqrt((venx[i]-venx[i-1])**2 + (veny[i]-veny[i-1])**2)
        venvelocity[i] = venpythag[i]

    x.append(venx), y.append(veny), velocity.append(venvelocity), days.append(vendays)



def Earth_orbit():
    L = 2.7 * 10 ** 40  # L = angular momentum
    m = 5.972 * 10 ** 24  # m = mass of earth
    M = 1.99 * 10 ** 30  # M = mass of sun
    a = 14.9 * 10 ** 10  # a = semi-major axis
    G = 6.674 * 10 ** -11  # G = Gravitational constant
    k = G * M * m
    E = -k / (2 * a)  # E = energy
    p = L ** 2 / (m * k)
    c = 1 + (2 * E * L ** 2) / (m * k ** 2)
    e = 0.017  # e = eccentricity

    def fx(x):
        r = p / (1 + e * cos(x))
        return r

    phi = linspace(0, 2 * pi, days_earth)
    earpythag = zeros([days_earth])
    earvelocity = zeros([days_earth])
    radius = zeros([days_earth])
    theta = zeros([days_earth])
    earx = zeros([days_earth])
    eary = zeros([days_earth])

    for i in range(0, days_earth):
        radius[i] = fx(phi[i])
        theta[i] = 180 * phi[i] / pi

    for i in range(0, days_earth):
        earx[i] = radius[i] * cos(phi[i]) / 10000000
        eary[i] = radius[i] * sin(phi[i]) / 10000000

    eardays = []
    for i in range(0, days_earth):
        eardays.append(i+1)

    for i in range(1, days_earth):
        earvelocity[0] = 0
        earpythag[i] = sqrt((earx[i]-earx[i-1])**2 + (eary[i]-eary[i-1])**2)
        earvelocity[i] = earpythag[i]


    x.append(earx), y.append(eary), velocity.append(earvelocity), days.append(eardays)


def Mars_orbit():
    L = 3.5 * 10 ** 39  # L = angular momentum
    m = 6.42 * 10 ** 23  # m = mass of mars
    M = 1.99 * 10 ** 30  # M = mass of sun
    a = 22.8 * 10 ** 10  # a = semi-major axis
    G = 6.674 * 10 ** -11  # G = Gravitational constant
    k = G * M * m
    E = -k / (2 * a)  # E = energy
    p = L ** 2 / (m * k)
    c = 1 + (2 * E * L ** 2) / (m * k ** 2)
    e = 0.0934  # e = eccentricity

    def fx(x):
        r = p / (1 + e * cos(x))
        return r

    phi = linspace(0, 2 * pi, days_mars)
    marpythag = zeros([days_mars])
    marvelocity = zeros([days_mars])
    radius = zeros([days_mars])
    theta = zeros([days_mars])
    marx = zeros([days_mars])
    mary = zeros([days_mars])

    for i in range(0, days_mars):
        radius[i] = fx(phi[i])
        theta[i] = 180 * phi[i] / pi
        marvelocity[i] = radius[i] * L

    for i in range(0, days_mars):
        marx[i] = radius[i] * cos(phi[i]) / 10000000
        mary[i] = radius[i] * sin(phi[i]) / 10000000

    mardays = []
    for i in range(0, days_mars):
        mardays.append(i+1)

    for i in range(1, days_mars):
        marvelocity[0] = 0
        marpythag[i] = sqrt((marx[i]-marx[i-1])**2 + (mary[i]-mary[i-1])**2)
        marvelocity[i] = marpythag[i] / mardays[i]            

    x.append(marx), y.append(mary), velocity.append(marvelocity), days.append(mardays)


def Jupiter_orbit():
    L = 1.9 * 10 ** 43  # L = angular momentum
    m = 1.9 * 10 ** 27  # m = mass of jupiter
    M = 1.99 * 10 ** 30  # M = mass of sun
    a = 77.8 * 10 ** 10  # a = semi-major axis
    G = 6.674 * 10 ** -11  # G = Gravitational constant
    k = G * M * m
    E = -k / (2 * a)  # E = energy
    p = L ** 2 / (m * k)
    c = 1 + (2 * E * L ** 2) / (m * k ** 2)
    e = 0.049  # e = eccentricity

    def fx(x):
        r = p / (1 + e * cos(x))
        return r

    phi = linspace(0, 2 * pi, days_jupiter)
    jupvelocity = zeros([days_jupiter])
    juppythag = zeros([days_jupiter])
    radius = zeros([days_jupiter])
    theta = zeros([days_jupiter])
    jupx = zeros([days_jupiter])
    jupy = zeros([days_jupiter])

    for i in range(0, days_jupiter):
        radius[i] = fx(phi[i])
        theta[i] = 180 * phi[i] / pi

    for i in range(0, days_jupiter):
        jupx[i] = radius[i] * cos(phi[i]) / 10000000
        jupy[i] = radius[i] * sin(phi[i]) / 10000000

    jupdays = []
    for i in range(0, days_jupiter):
        jupdays.append(i+1)

    for i in range(1, days_mars):
        jupvelocity[0] = 0
        juppythag[i] = sqrt((jupx[i]-jupx[i-1])**2 + (jupy[i]-jupy[i-1])**2)
        jupvelocity[i] = juppythag[i]

    x.append(jupx), y.append(jupy), velocity.append(jupvelocity), days.append(jupdays)



def Saturn_orbit():
    L = 7.8 * 10 ** 42  # L = angular momentum
    m = 5.68 * 10 ** 26  # m = mass of Saturn
    M = 1.99 * 10 ** 30  # M = mass of sun
    a = 143.2 * 10 ** 10  # a = semi-major axis
    G = 6.674 * 10 ** -11  # G = Gravitational constant
    k = G * M * m
    E = -k / (2 * a)  # E = energy
    p = L ** 2 / (m * k)
    c = 1 + (2 * E * L ** 2) / (m * k ** 2)
    e = 0.057  # e = eccentricity

    def fx(x):
        r = p / (1 + e * cos(x))
        return r

    phi = linspace(0, 2 * pi, days_saturn)
    satvelocity = zeros([days_saturn])
    satpythag = zeros([days_saturn])
    radius = zeros([days_saturn])
    theta = zeros([days_saturn])
    satx = zeros([days_saturn])
    saty = zeros([days_saturn])

    for i in range(0, days_saturn):
        radius[i] = fx(phi[i])
        theta[i] = 180 * phi[i] / pi

    for i in range(0, days_saturn):
        satx[i] = radius[i] * cos(phi[i]) / 10000000
        saty[i] = radius[i] * sin(phi[i]) / 10000000

    satdays = []
    for i in range(0, days_saturn):
        satdays.append(i+1)

    for i in range(1, days_mars):
        satvelocity[0] = 0
        satpythag[i] = sqrt((satx[i]-satx[i-1])**2 + (saty[i]-saty[i-1])**2)
        satvelocity[i] = satpythag[i]

    x.append(satx), y.append(saty), velocity.append(satvelocity), days.append(satdays)


def Uranus_orbit():
    L = 1.7 * 10 ** 42  # L = angular momentum
    m = 8.68 * 10 ** 25  # m = mass of Uranus
    M = 1.99 * 10 ** 30  # M = mass of sun
    a = 286.7 * 10 ** 10  # a = semi-major axis
    G = 6.674 * 10 ** -11  # G = Gravitational constant
    k = G * M * m
    E = -k / (2 * a)  # E = energy
    p = L ** 2 / (m * k)
    c = 1 + (2 * E * L ** 2) / (m * k ** 2)
    e = 0.046  # e = eccentricity

    def fx(x):
        r = p / (1 + e * cos(x))
        return r

    phi = linspace(0, 2 * pi, days_uranus)
    uravelocity = zeros([days_uranus])
    urapythag = zeros([days_uranus])
    radius = zeros([days_uranus])
    theta = zeros([days_uranus])
    urax = zeros([days_uranus])
    uray = zeros([days_uranus])

    for i in range(0, days_uranus):
        radius[i] = fx(phi[i])
        theta[i] = 180 * phi[i] / pi

    for i in range(0, days_uranus):
        urax[i] = radius[i] * cos(phi[i]) / 10000000
        uray[i] = radius[i] * sin(phi[i]) / 10000000

    uradays = []
    for i in range(0, days_uranus):
        uradays.append(i+1)

    for i in range(1, days_mars):
        uravelocity[0] = 0
        urapythag[i] = sqrt((urax[i]-urax[i-1])**2 + (uray[i]-uray[i-1])**2)
        uravelocity[i] = urapythag[i]

    x.append(urax), y.append(uray), velocity.append(uravelocity), days.append(uradays)


def Neptune_orbit():
    L = 2.5 * 10 ** 42  # L = angular momentum
    m = 1.02 * 10 ** 26  # m = mass of Neptune
    M = 1.99 * 10 ** 30  # M = mass of sun
    a = 451.5 * 10 ** 10  # a = semi-major axis
    G = 6.674 * 10 ** -11  # G = Gravitational constant
    k = G * M * m
    E = -k / (2 * a)  # E = energy
    p = L ** 2 / (m * k)
    c = 1 + (2 * E * L ** 2) / (m * k ** 2)
    e = 0.011  # e = eccentricity

    def fx(x):
        r = p / (1 + e * cos(x))
        return r

    phi = linspace(0, 2 * pi, days_neptune)
    nepvelocity = zeros([days_neptune])
    neppythag = zeros([days_neptune])
    radius = zeros([days_neptune])
    theta = zeros([days_neptune])
    nepx = zeros([days_neptune])
    nepy = zeros([days_neptune])

    for i in range(0, days_neptune):
        radius[i] = fx(phi[i])
        theta[i] = 180 * phi[i] / pi

    for i in range(0, days_neptune):
        nepx[i] = radius[i] * cos(phi[i]) / 10000000
        nepy[i] = radius[i] * sin(phi[i]) / 10000000

    nepdays = []
    for i in range(0, days_neptune):
        nepdays.append(i+1)

    for i in range(1, days_mars):
        nepvelocity[0] = 0
        neppythag[i] = sqrt((nepx[i]-nepx[i-1])**2 + (nepy[i]-nepy[i-1])**2)
        nepvelocity[i] = neppythag[i]
    
    x.append(nepx), y.append(nepy), velocity.append(nepvelocity), days.append(nepdays)

Sun
Mercury_orbit()
Venus_orbit()
Earth_orbit()
Mars_orbit()
Jupiter_orbit()
Saturn_orbit()
Uranus_orbit()
Neptune_orbit()

matplotlib.pyplot.figure(figsize=(20,20))

for num in range(len(days)):
    matplotlib.pyplot.plot(days[num],velocity[num], linewidth=5)
