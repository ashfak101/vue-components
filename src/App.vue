<script setup lang="ts">
import { ref } from 'vue'
import { Button } from '@/components/ui/button'
import { Spinner } from '@/components/ui/spinner'
import { Avatar, AvatarImage, AvatarFallback } from '@/components/ui/avatar'
import { Input } from '@/components/ui/input'
import { Checkbox } from '@/components/ui/checkbox'
import { Switch } from '@/components/ui/switch'
import { Alert, AlertTitle, AlertDescription } from '@/components/ui/alert'
import { Card, CardHeader, CardTitle, CardDescription, CardContent, CardFooter } from '@/components/ui/card'
import { Dialog, DialogTrigger, DialogContent, DialogHeader, DialogTitle, DialogDescription, DialogFooter } from '@/components/ui/dialog'
import { Table, TableHeader, TableBody, TableRow, TableHead, TableCell } from '@/components/ui/table'
import { Pagination, PaginationList, PaginationPrev, PaginationNext } from '@/components/ui/pagination'
import { Accordion, AccordionItem, AccordionTrigger, AccordionContent } from '@/components/ui/accordion'
import { Sidebar } from '@/components/ui/sidebar'
import { Select, SelectContent, SelectGroup, SelectItem, SelectTrigger, SelectValue } from '@/components/ui/select'
import { Stack, Grid, Container } from '@/components/ui/layout'
import { FormItem, FormLabel } from '@/components/ui/form'
import { Badge } from '@/components/ui/badge'
import { DataList, DataItem } from '@/components/ui/data-list'
import { MedicalStat } from '@/components/ui/hms'
import { Toast } from '@/components/ui/toast'
import { LayoutDashboard, Users, Settings, Bell, Search, Plus, Info, CheckCircle2, AlertCircle, Heart, Activity, Thermometer, User, CalendarDays } from 'lucide-vue-next'

const search = ref('')
const isChecked = ref(false)
const isToggled = ref(true)
const isLoading = ref(false)

const simulateLoading = () => {
  isLoading.value = true
  setTimeout(() => {
    isLoading.value = false
  }, 2000)
}
</script>

<template>
  <div class="flex h-screen bg-background">
    <!-- Sidebar -->
    <Sidebar class="hidden md:flex">
      <div class="p-6">
        <h2 class="text-lg font-bold tracking-tight">Antigravity UI</h2>
      </div>
      <nav class="flex-1 space-y-1 px-3">
        <a href="#" class="flex items-center rounded-md bg-accent px-3 py-2 text-sm font-medium text-accent-foreground">
          <LayoutDashboard class="mr-3 h-4 w-4" />
          Dashboard
        </a>
        <a href="#" class="flex items-center rounded-md px-3 py-2 text-sm font-medium hover:bg-accent hover:text-accent-foreground">
          <Users class="mr-3 h-4 w-4" />
          Users
        </a>
        <a href="#" class="flex items-center rounded-md px-3 py-2 text-sm font-medium hover:bg-accent hover:text-accent-foreground">
          <Settings class="mr-3 h-4 w-4" />
          Settings
        </a>
      </nav>
      <div class="p-4 border-t">
        <div class="flex items-center gap-3">
          <Avatar>
            <AvatarImage src="https://github.com/shadcn.png" alt="@shadcn" />
            <AvatarFallback>CN</AvatarFallback>
          </Avatar>
          <div class="flex flex-col">
            <span class="text-sm font-medium">Shad Vue</span>
            <span class="text-xs text-muted-foreground">admin@example.com</span>
          </div>
        </div>
      </div>
    </Sidebar>

    <!-- Main Content -->
    <main class="flex-1 overflow-y-auto">
      <header class="sticky top-0 z-10 border-b bg-background/95 backdrop-blur">
        <div class="flex h-16 items-center justify-between px-8">
          <div class="flex items-center gap-4 flex-1">
            <div class="relative w-full max-w-sm">
              <Search class="absolute left-2.5 top-2.5 h-4 w-4 text-muted-foreground" />
              <Input v-model="search" placeholder="Search components..." class="pl-9" />
            </div>
          </div>
          <div class="flex items-center gap-4">
            <Button variant="ghost" size="icon">
              <Bell class="h-4 w-4" />
            </Button>
            <Dialog>
              <DialogTrigger as-child>
                <Button>
                  <Plus class="mr-2 h-4 w-4" />
                  New Entry
                </Button>
              </DialogTrigger>
              <DialogContent>
                <DialogHeader>
                  <DialogTitle>Create New Entry</DialogTitle>
                  <DialogDescription>
                    Add a new item to your dashboard library.
                  </DialogDescription>
                </DialogHeader>
                <div class="grid gap-4 py-4">
                  <FormItem>
                    <FormLabel>Name</FormLabel>
                    <Input placeholder="Enter name..." />
                  </FormItem>
                  <FormItem>
                    <FormLabel>Category</FormLabel>
                    <Input placeholder="Enter category..." />
                  </FormItem>
                </div>
                <DialogFooter>
                  <Button type="submit">Save changes</Button>
                </DialogFooter>
              </DialogContent>
            </Dialog>
          </div>
        </div>
      </header>

      <Container class="p-8">
        <Stack gap="8">
          <!-- Dashboard Hero -->
          <Grid :cols="4" gap="4">
            <Card>
            <CardHeader class="flex flex-row items-center justify-between space-y-0 pb-2">
              <CardTitle class="text-sm font-medium">Total Users</CardTitle>
              <Users class="h-4 w-4 text-muted-foreground" />
            </CardHeader>
            <CardContent>
              <div class="text-2xl font-bold">1,234</div>
              <p class="text-xs text-muted-foreground">+12% from last month</p>
            </CardContent>
          </Card>
          <Card>
            <CardHeader class="flex flex-row items-center justify-between space-y-0 pb-2">
              <CardTitle class="text-sm font-medium">Active Now</CardTitle>
              <LayoutDashboard class="h-4 w-4 text-muted-foreground" />
            </CardHeader>
            <CardContent>
              <div class="text-2xl font-bold">+573</div>
              <p class="text-xs text-muted-foreground">+201 since last hour</p>
            </CardContent>
          </Card>
          <Card>
            <CardHeader class="flex flex-row items-center justify-between space-y-0 pb-2">
              <CardTitle class="text-sm font-medium">Success Rate</CardTitle>
              <CheckCircle2 class="h-4 w-4 text-muted-foreground" />
            </CardHeader>
            <CardContent>
              <div class="text-2xl font-bold">99.9%</div>
              <p class="text-xs text-muted-foreground">Stable performance</p>
            </CardContent>
          </Card>
          <Card>
            <CardHeader class="flex flex-row items-center justify-between space-y-0 pb-2">
              <CardTitle class="text-sm font-medium">Alerts</CardTitle>
              <AlertCircle class="h-4 w-4 text-muted-foreground" />
            </CardHeader>
            <CardContent>
              <div class="text-2xl font-bold">12</div>
              <p class="text-xs text-muted-foreground">3 require attention</p>
            </CardContent>
          </Card>
          </Grid>
 
          <!-- HMS Specific Section -->
          <Stack gap="4">
            <h3 class="text-lg font-semibold px-1">Patient Vitals & Profile</h3>
            <Grid :cols="4" gap="4">
              <MedicalStat
                title="Heart Rate"
                value="72"
                unit="bpm"
                :trend="{ value: '+2%', type: 'up' }"
                :icon="Heart"
                class="border-red-100 bg-red-50/30"
              />
              <MedicalStat
                title="Blood Pressure"
                value="120/80"
                unit="mmHg"
                description="Normal range"
                :icon="Activity"
                class="border-blue-100 bg-blue-50/30"
              />
              <MedicalStat
                title="Body Temp"
                value="98.6"
                unit="°F"
                :trend="{ value: 'Stable', type: 'neutral' }"
                :icon="Thermometer"
                class="border-orange-100 bg-orange-50/30"
              />
              <MedicalStat
                title="Oxygen Level"
                value="98"
                unit="%"
                :trend="{ value: '-1%', type: 'down' }"
                :icon="Info"
                class="border-green-100 bg-green-50/30"
              />
            </Grid>

            <Card>
              <CardHeader>
                <div class="flex items-center justify-between">
                  <div class="flex items-center gap-4">
                    <Avatar size="lg">
                      <AvatarImage src="https://api.dicebear.com/7.x/avataaars/svg?seed=John" />
                      <AvatarFallback>JD</AvatarFallback>
                    </Avatar>
                    <div>
                      <CardTitle>John Doe</CardTitle>
                      <CardDescription>Patient ID: #PAT-2024-001</CardDescription>
                    </div>
                  </div>
                  <Badge variant="success">Admitted</Badge>
                </div>
              </CardHeader>
              <CardContent>
                <DataList>
                  <DataItem label="Age">32 Years</DataItem>
                  <DataItem label="Blood Group">O+ Positive</DataItem>
                  <DataItem label="Last Visit">12 May 2024</DataItem>
                  <DataItem label="Doctor In Charge">
                    <Select default-value="sarah">
                      <SelectTrigger class="w-[200px]">
                        <SelectValue placeholder="Select a doctor" />
                      </SelectTrigger>
                      <SelectContent>
                        <SelectGroup>
                          <SelectItem value="sarah">Dr. Sarah Wilson</SelectItem>
                          <SelectItem value="michael">Dr. Michael Chen</SelectItem>
                          <SelectItem value="emily">Dr. Emily Adams</SelectItem>
                        </SelectGroup>
                      </SelectContent>
                    </Select>
                  </DataItem>
                </DataList>
              </CardContent>
            </Card>
          </Stack>

        <!-- Components Grid -->
        <Grid :cols="2" gap="8">
          <!-- Left Column -->
          <Stack gap="8">
            <Card>
              <CardHeader>
                <CardTitle>Interactive Elements</CardTitle>
                <CardDescription>Buttons, Toggles, and Form controls.</CardDescription>
              </CardHeader>
              <CardContent class="space-y-6">
                <div class="flex flex-wrap gap-4">
                  <Button @click="simulateLoading" :disabled="isLoading">
                    <Spinner v-if="isLoading" class="mr-2 h-4 w-4" />
                    {{ isLoading ? 'Processing...' : 'Primary Button' }}
                  </Button>
                  <Button variant="secondary">Secondary</Button>
                  <Button variant="destructive">Destructive</Button>
                  <Button variant="outline">Outline</Button>
                  <Button variant="ghost">Ghost</Button>
                </div>
                <div class="flex items-center space-x-8">
                  <div class="flex items-center space-x-2">
                    <Checkbox id="terms" v-model:checked="isChecked" />
                    <label for="terms" class="text-sm font-medium leading-none">Accept terms</label>
                  </div>
                  <div class="flex items-center space-x-2">
                    <Switch id="airplane-mode" v-model:checked="isToggled" />
                    <label for="airplane-mode" class="text-sm font-medium leading-none">Airplane Mode</label>
                  </div>
                </div>
                <div class="space-y-2">
                  <FormLabel>Sample Input</FormLabel>
                  <Input placeholder="Type something..." />
                </div>
              </CardContent>
            </Card>

            <Alert variant="info">
              <Info class="h-4 w-4" />
              <AlertTitle>System Update</AlertTitle>
              <AlertDescription>
                A new version of the component library is available.
              </AlertDescription>
            </Alert>
          </Stack>

          <!-- Right Column -->
          <Stack gap="8">
            <Card>
              <CardHeader>
                <CardTitle>Data Display</CardTitle>
                <CardDescription>Tables and Accordions.</CardDescription>
              </CardHeader>
              <CardContent class="space-y-6">
                <Table>
                  <TableHeader>
                    <TableRow>
                      <TableHead>User</TableHead>
                      <TableHead>Status</TableHead>
                      <TableHead>Role</TableHead>
                    </TableRow>
                  </TableHeader>
                  <TableBody>
                    <TableRow>
                      <TableCell class="font-medium">Alex Rivera</TableCell>
                      <TableCell><span class="text-green-500 font-semibold">Active</span></TableCell>
                      <TableCell>Admin</TableCell>
                    </TableRow>
                    <TableRow>
                      <TableCell class="font-medium">Jordan Smith</TableCell>
                      <TableCell><span class="text-yellow-500 font-semibold">Idle</span></TableCell>
                      <TableCell>Editor</TableCell>
                    </TableRow>
                  </TableBody>
                </Table>

                <Accordion type="single" collapsible class="w-full">
                  <AccordionItem value="item-1">
                    <AccordionTrigger>Is it accessible?</AccordionTrigger>
                    <AccordionContent>
                      Yes. It adheres to the WAI-ARIA design patterns.
                    </AccordionContent>
                  </AccordionItem>
                  <AccordionItem value="item-2">
                    <AccordionTrigger>Is it styled?</AccordionTrigger>
                    <AccordionContent>
                      Yes. It comes with default styles that match the rest of your app.
                    </AccordionContent>
                  </AccordionItem>
                </Accordion>
              </CardContent>
              <CardFooter>
                <Pagination :total="100" :sibling-count="1" show-edges :default-page="1">
                  <PaginationList class="flex items-center gap-1">
                    <PaginationPrev />
                    <PaginationNext />
                  </PaginationList>
                </Pagination>
              </CardFooter>
            </Card>

            <Toast title="Notification" description="Your profile has been updated successfully." />
          </Stack>
        </Grid>
      </Stack>
    </Container>
  </main>
</div>
</template>
